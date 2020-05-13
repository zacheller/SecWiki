---
description: Based on Autopsy Basics and Hands On (8-Hours) Course
---

# Autopsy - open-source digital forensics platform

### Typical Workflow

1. Create a case.

2. Add a data source.

3. Configure case-relevant keywords.

4. Run ingest with relevant modules.

5. Review data as it comes in.

6. Update keywords as you find more relevant terms.

7. Tag files of interest.

8. Generate report.

## Base Concepts

* Deployment options: "Desktop/Single-User" and "Cluster/Multi-User" with Central Repository
* Multi-user Autopsy deployment
  * Two types of databases supported by a Central Repository deployment: SQLite for single user, PostgreSQL for multiple
  * allows for "Auto-Ingest" mode, where new media is automatically analyzed 24 x 7 by multiple nodes and Analysis can be faster \(if you have fast hardware\)
  * One of the primary reasons for having the Central Repository is that it allows you to easily access metadata from past cases.
  * You can store hash sets in the Central Repository that can be shared by everyone in the lab.

## Installation

* You can have multiple versions of Autopsy installed on an endpoint at the same time.
* Running on OSX or Linux requires more manual steps that are outlined in Running\_Linux\_OSX.txt.
* For all Autopsy releases prior to Autopsy 4.15, the Central Repository is disabled by default.
* Central Shared Storage and 2 Servers are the minimum resources needed for a multi-user Autopsy deployment
* Autopsy needs to be installed on each examiner's computer, whether using a single-user or multi-user deployment
* Autopsy supports Machine Translation integration from Google and Microsoft

## Cases and Data Sources

* A case groups the investigation data you are going to analyze.
* Supported data sources
  * Disk Images
    * Raw \(dd\) single and split
    * E01
    * Raw disk images of phones \(Android\)
    * Virtual machine formats
  * Local Drives
    * Preview a live system \(i.e. triage\)
    * USB-attached device \(write blocker\)
  * Local Files \(Logical Files/Folders\)
    * JPEGs, Word docs
    * L01 file
  * Output from Autopsy Logical Imager
  * Unallocated Space Files \(no structure\)
* Populate the case database
  * File Metadata
  * Partition layouts
* Finding Orphan files in FAT file systems in time intensive
  * can be disabled when image is added
* PhotoRec - open-source carving tool
  * Carving recovers deleted files without relying on file system knowledge
  * Relies on file structure internals \(e.g. JPEG, PDF\)
  * Needed when File System doesn't have pointers to file content anymore
* Unallocated space is represented as files.
* Local Drive Analysis
  * need admin privileges on all drives
  * VHD File created that copies the drive as it goes
    * will be complete copy if you keep it running
* Local Files
  * not copied or moved
  * info about each file is added to DB
* In a multi-user cluster, all examiners need to have access to the case directory at the same path \(i.e. \server\cases or Z:\Cases\)
* Autopsy is able to ingest Disk Images/VM files and logical files directly.
* When adding a data source to Autopsy, in-depth analysis on the data is not automatically performed.
* The Autopsy case database does not store full copies of every single file contained within a data source.
* Autopsy supports many volume systems, including: DOS, BSD, GPT
* Orphan files, deleted file that no longer has a parent folder, are stored under the $OrphanFile folder.
* When adding "Local Files and Folders" to a case in Autopsy, file times aren't added to the database.
* When adding an E01 file to a case within Autopsy, the E01 file is not automatically validated upon import.

### Lab

Renzik has been dognapped. Ransom notes have been sent. Laptop is found in a car. Media card to be found later in search of house.

* Downloaded the disk images
  * device1\_laptop.e01
  * device2\_mediacard.e01
* Made case1 from device1\_laptop.e01
  * 6 volumes
  * Unallocated file in vol1: Unalloc\_3\_0\_1048576
  * vol7 is of type NTFS
  * Data Base File is called autopsy.db, ~225 MB

## UI Basics

* Notable tags get applied with a Hash hit
* Suspicious tags are marked by a module as interesting
* Comments, Occurrences if file seen in past cases \(requires Central Repo\)
* File names and text can be translated
* Hex viewer, Text/Strings, Application viewer, Message viewer, Metadata, Analysis results, Annotations, Occurences
* Video Triage, takes snapshots of a video so you can quickly check relevance
* Ingest inbox for when ingest modules find something but don't want to disturb you
* Timeline - displays events sorted by time
* Image Gallery - photos, videos grouped by folder
* Communications - accounts, messages, call logs, etc

### Lab

* By extension, how many databases are there?
  * 59
* What is the size of the largest database?
  * 5242880
* Are there any databases by MIME type yet?
  * No, because file types have not been yet determined.
* What are the names of the files between 200MB and 1GB in size?
  * chrome.7z, Winre.wim, $BadClus:$Bad

## Analyzing Data Sources

* Ingest Modules - plug-ins responsible for analyzing the data on the drive
  * Two types:
    * File Ingest Modules
    * Data Source Ingest Modules
  * Ingest modules can run in parallel
  * Save their results as Blackboard Artifacts \(Type, Value pair\)
    * one or more attributes
    * Saved under "Extracted Content"
    * e.g. Web Bookmark, Hash Hit, Encryption Detected
  * Autopsy prioritizes files so that important ones are analyzed first.  The priority order is: 
    * User Folders
    * Program Files and other root folders
    * Windows folder
    * Unallocated space

## Hash Lookup Module

* The "Hash Lookup" can calculate the MD5 hash of a file.
* Why?
  * Identify notable \("known bad"\) files
  * Hide known files from UI
  * Make ingest faster
* Files found in a hash set will be in the Hashset Hits part of the tree
* An index allows Autopsy to lookup hash values faster.
* Supports: EnCase, NIST NSRL, md5sum, Hashkeeper, .kdb files

### Lab

We are now going to begin analyzing the laptop. We are starting off the case with some clues. Most notably, we have pictures that were sent with the ransom emails to Basis Technology

* Right click on device1\_laptop.e01 image in tree and choose “Run Ingest Modules”
* Enable Hash Lookup, File Type Identification, Extension Mismatch Detector, Embedded File Extractor, Exif Parser, Email Parser, Correlation Engine
* Configure the Hash Lookup module with two hash sets:
  * NSRL File
  * New Hash set that just contains the hash for the ransom note
    * 07c94320f4e41291f855d450f68c8c5b
* Hash hits: “RN.jpg” and “f\_000239”
* 6 total hits are found under the “Hashset Hits” results after running the Hash Lookup Ingest Module
* 7 total ".jpg" files are in the folder “Pictures” where the notable hash hit was found

## Various Small Modules

* Modules
  * File Type Module: determines MIME types based on signatures
    * define custom file types \(Tools -&gt; Options -&gt; File Types\)
      * specify MIME type \(or make one\), offset of signature, signature
  * File Extension Mismatch Module \(false positives due to renames: .tmp, .bak, .0, .1\)
  * Exif Module - extracts Exif structure from JPEGs
    * identify camera type, time of pic, geo-coordinates
  * Embedded File Extractor - opens ZIP, RAR, other archives
    * will flag a file if it is password protected
    * you can supply the password by right clicking on the file
  * Email Module - identify email based communications
  * Interesting Files Module - flags files and folders you configure to be "interesting"
    * alerts for iPhone backups, VMWare images, Bitcoin wallets, cloud storage clients
  * Encryption Detection Module - flags files and volumes that are or could be encrypted
    * looks for High entropy, multiple of 512 bytes, no distinguishable file type
  * Plaso Module - parse logs and file types to extract time stamps for timeline
    * ironically very time intensive, disabled by default
  * VM Extractor Module - detects, copies, and feeds them back in as data sources
  * Data Source Integrity Module - validates and calculates hash of disk image
    * ensure integrity of evidence, generates an alert if different
* MIME type "application/octet-stream" designates unknown type

### Lab

* Search images by camera type
  * iPhone 7 Plus:         1 picture
  * Samsung Galaxy S8:     0 pictures
  * BLU R1 HD:            15 pictures
* 113 Extension mismatches detected
  * .rsrc -&gt; image/png
  * .dat -&gt; application/x-msoffice
  * .bytes -&gt; image/png
* Ran Interesting Files module looking for "veracrypt.exe" and "truecrypt.exe"
  * found VeraCrypt.exe

## Recent Activity Module

* Web Activity \(depending on Browser\)
  * History
  * Bookmarks
  * Cookies
  * Downloads
  * Cache
  * Addresses and Web Form autofill
* Registry Analysis using RegRipper
  * USB Devices
  * User accounts
  * Installed Programs
  * Programs Run
* Recycle Bin Analysis

### Lab

* 5 Web Bookmarks
* Twitter Account username: AntiRenzik
* Randomizer ransom note generator is suspicious URL
* YouTube Cookies all made on November 12, 2019
* how to treat a dog bite searched on November 12, 2019
* how to make a ransom note searched on November 5, 2019
* hostage negotiation tactics searched on November 5, 2019
* antirenzik@gmail.com
* 2 flash drives, 9 VMs
* 3 items in recycle bin

## Keyword Search Module

* Updates and searches a text index to enable text-based searching
* Uses Apache Solr and Apache Tika
* A text index is an organized collection of words and the files that contain them.

### Lab

* in order to ensure that renzik is treated properly.docx
* 10 hits for “Renzik” in NTUSER.DAT

## Correlation Engine Module

* Queries Central Repository, to see if items in current case were previously seen, and adds data to Central Repository
* Repo stores:
  * Value
  * Case
  * Data Source
  * File Path
  * User-supplied Comment
  * Notable Status
* There is one row in the Central Repository for every instance of a property

### Lab

At this point in the scenario, the police have searched the house and, with the help of Siri the electronic sniffing K9, found a media card. We will add that to our case and find some correlations.

* IMG\_20191024\_155744.jpg was found on both.
  * 2019-10-24 on media card
  * 2019-11-01 on laptop
* Also showed up as f\_00022e on laptop

## Andriod Analyzer Module

* Locates SQLite DBs and files from Andriod and 3rd party apps
  * Call Logs
  * Contacts
  * Messages
  * Browsers
  * File Transfer
  * Geo

## Timeline Analysis

* The timeline feature allows an analyst to view a graphical representation of time based events that occurred on a system
* Main areas: Filters, Events, Files and Content
* In the List View, the letter "A" under Event Type stands for Last Accessed
* In the List View, the letter "B" under Event Type stands for Date Created

## Image Gallery

* Allows you tomore easily review sets of images and videos
* Folders are prioritized by density of hash hits and total number of images
* Add-on for Law Enforcement: integrate with DBs incl. Project Vic and C4ALL

## Communications UI

* Oriented around Accounts over data types
  * Data extracted from Andriod Analyzer and Email Parser
* Review relationships between Accounts and Device Accounts
  * A special account that is created by Autopsy for a data source when it doesn't know what account was used is called a Device account
* Accounts in Autopsy have both a "type" and a unique "identifier"
* By default, accounts are sorted by the number of relationships they have in the case. 

## Tagging, Commenting, and Reporting

* Tagging allows a user to reference a file or object to easily find it later
* When viewing a result \(aka a Blackboard Artifact\) you have the choice to tag either the result or its source file
* In a multi-user environment, tags are associated with the examiner who made them
* You can tag a specific part of an image
* Generate a Portable case: includes only tagged files and interesting item hits

## Installing 3rd Party Modules

* Official Repo: [autopsy\_addon\_modules](https://github.com/sleuthkit/autopsy_addon_modules)
* Java: Tools -&gt; Plugins menu, then just Add Plugin and Install
* Python: Copy module folder into the python\_modules folder


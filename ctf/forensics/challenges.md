# Challenges

#### Allergic College Application

Description: I was writing my common app essay in Mandarin when my cat got on my lap and sneezed. Being allergic, I sneezed with him, and when I blew my nose into a tissue, the text for my essay turned really weird! Get out, Bad Kitty!

```
$ python3
>>> f = open ('app', encoding='gb2312').readlines()
>>> f
end of output: {我_只_修改_了_两_次}
OR
cat app | iconv -f GBK -t UTF-8

rtcp{我_只_修改_了_两_次}
```

#### BTS-Crazed

Description: My friend made this cool remix, and it's pretty good, but everyone says there's a deeper meaning in the music. To be honest, I can't really tell - the second drop's 808s are just too epic. [https://github.com/JEF1056/riceteacatpanda/raw/master/BTS-Crazed (75)/Save Me.mp3](https://github.com/JEF1056/riceteacatpanda/raw/master/BTS-Crazed%20\(75\)/Save%20Me.mp3)

```
$ strings Save\ Me.mp3 | grep -oE "rtcp{.*}"
rtcp{j^cks0n_3ats_r1c3}
```

#### cat-chat

Description: nyameowmeow nyameow nyanya meow purr nyameowmeow nyameow nyanya meow purr nyameowmeow nyanyanyanya nyameow meow purr meow nyanyanyanya nya purr nyanyanyanya nya meownyameownya meownyameow purr nyanya nyanyanya purr meowmeownya meowmeowmeow nyanya meownya meowmeownya purr meowmeowmeow meownya purr nyanyanyanya nya nyameownya nya !!!!&#x20;

nya and meow are repeated a lot together, trial and error led to nya being . and meow being -\
I tested and wrote a sed command to parse cat-chat into morse which I saved into meow\_to\_morse.sh: sed 's/nya/./g;s/meow/-/g;s/purr//g'\
\
I downloaded a morse decoder from git.\


```
git clone https://github.com/mk12/morse.git
 /opt/morse
cd $_
make
ln -s /opt/morse/bin/morse ~/bin/morse
```

I also copied all the chat from the discord channel into the file `meows.txt`.

```
$ cat meows.txt | ./meow_to_morse.sh | morse -d | grep RTCP | sed 's/?/_/g' #output is in all caps
RTCP:TH15_1Z_A_C4T_CH4T_N0T_A_M3M3_CH4T

rtcp{TH15_1Z_A_C4T_CH4T_N0T_A_M3M3_CH4T}
```

#### catch-at

Description: 636274425917865984\
Navigate to [https://discordapp.com/channels/624036526157987851/633364891616411667/636274425917865984](https://discordapp.com/channels/624036526157987851/633364891616411667/636274425917865984)\
Copy output from message at the id 636274425917865984:

```
$ echo "meowmeowmeow nyanyanyanya purr meownyanyanya meownyameowmeow purr meow nyanyanyanya nya purr nyameowmeow nyameow meownyameowmeow meowmeownyanyameowmeow purr nyanyanyanya nya nyameownya nya nyameowmeowmeowmeownya nyanyanya purr nyameow purr nyameownyanya nyanya meow meow nyameownyanya nya purr nyanyanya meowmeowmeow meowmeow nya meow nyanyanyanya nyanya meownya meowmeownya meowmeowmeownyanyanya purr nyameowmeow meowmeowmeowmeowmeow nyameowmeow nyanyameowmeownyameow meownyanya nyameowmeowmeowmeow nyanyanyanyanya meownyameownya meowmeowmeowmeowmeow nyameownya meownyanya nyanyameowmeownyameow nyanyanyanya nyanyanyanyameow nyanyanya nyanyameowmeownyameow nyanyanya nyanyanyameowmeow nyanyanyanyameow nyameownya meownyameownya nyanyanyanya nyanyameowmeownyameow nyanyameownya nyanyanyameowmeow nyanyanyanyameow meow nyanyameow nyameownya nyanyanyameowmeow nyanyanyanyanya" | ./meow_to_morse.sh | morse -d | sed 's/?/_/g'
OHBYTHEWAY,HERE'SALITTLESOMETHING:W0W_D15C0RD_H4S_S34RCH_F34TUR35

rtcp{W0W_D15C0RD_H4S_S34RCH_F34TUR35}
```

#### Chugalug's Footpads

Description: Chugalug makes footpads that he can chug and lug. However, his left one is different from his right... I wonder why?

```
$ xxd -c1 left.jpg > l && xxd -c1 right.jpg > r
$ grep -Fxvf r l | cut -d " " -f4 | tr -d "\n"
rtcp{Th3ze_^r3_n0TcH4nC1a5}
```

#### BASmati ricE 64

Description: There's a flag in that bowl somewhere... Replace all zs with \_ in your flag and wrap in rtcp{...}.

```
$ steghide extract -sf rice.jpg -xf extracted.txt
$ cat extracted.txt | base64 | sed 's/z/_/g' s0m3t1m35_th1ng5_Ar3_3nc0D3d
rtcp{s0m3t1m35_th1ng5_Ar3_3nc0D3d}
```

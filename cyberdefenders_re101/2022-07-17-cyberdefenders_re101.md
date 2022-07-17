
Challenge name: RE101 from CyberDefenders.

Link: [Link](https://cyberdefenders.org/blueteam-ctf-challenges/36)



# 1
Open the sample `malware000` in `pestudio` and then discover its strings. We see a Base64 encrypted string. 

<p align="center">
  <img src="/cyberdefenders_re101/img/1.png" />
</p>
<br>

Then Decrypt the Base64 string using [CyberChief](https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)&input=Wm14aFp6d3diM0J6WDJsZmRYTmxaRjh4TXpNM1gySTJORjlsYm1OeWVYQjBhVzl1UGdvPQ). The first flag shows up.


>  0ops_i_used_1337_b64_encryption

# 2

The second challenge is `Just some JS`. Which is not normal Js, it's [JSFuck Language](https://en.wikipedia.org/wiki/JSFuck). Open the file with any text editor and copy the code and decode it using this [site](https://www.dcode.fr/jsfuck-language). Then the flag shows up.

>  what_a_cheeky_language!1!

# 3
The 3rd one is `this_is_not_js`. Which is not normal JS too, it's [Brainfuck](https://en.wikipedia.org/wiki/Brainfuck) language. Open the file with any text editor and copy the code and decode it using this [site](https://www.dcode.fr/brainfuck-language). Then the flag shows up.

> Now_THIS_is_programming

# 4
The 4th one is `file.zip_broken` which is broken zip. Its header is broken. So we need to know the normal zip header which has a file looks like. See this [slides](https://slideplayer.com/slide/3421471/) for better unerstanding.

<p align="center">
  <img src="/cyberdefenders_re101/img/2.png" />
</p>
<br>
<p align="center">
  <img src="/cyberdefenders_re101/img/3.png" />
</p>
<br>

So the file inside the zip is flag.txt which is 8 chars. Open the `file.zip_broken` in hex editor  such as `HXD` editor. As in the previous figure, In the second row and 0A, 0B column. edit the value from of **58 58** to **08 00** because the name of the file in the zip is 8 chars (flag.txt). Then save the as .zip file then unzip using `password` then open the flag.txt

>  R3ad_th3_spec

# 5

the 5th challenge `malware101`. Open the file in IDA then go to the `main` function. This anti-analysis technique is called `stack strings`. 

<p align="center">
  <img src="/cyberdefenders_re101/img/4.png" />
</p>
<br>

So based on this, we don't need a debugger to get the output. The strings we obtain from this technique is `garins<ksaT__lfstLCAOg>M`, if we try to get a sence flag which is `flag<sTaCk_strings_LMAO>`. LMAO is an abbreviation of the phrase laughing my ass off.



> sTaCk_strings_LMAO

# 6
The 6th challenge `malware101`. Open the file in IDA then go to the `main` function. We see this `The encrypted flag is:` and `unk_40082B` has the encrypted flag.
<p align="center">
  <img src="/cyberdefenders_re101/img/5.png" />
</p>
<br>

Enter `unk_40082B` and copy its value. The value is the encypted flag.

encry_flag=[0x6d,0x78,0x61,0x6c,0xdd,0x7e,0x65,0x7e,0x47,0x6a,0x4f,0xcc,0xf7,0xca,0x73,0x68,0x55,0x42,0x53,0xdc,0xd7,0xd4,0x6b,0xec,0xdb,0xd2,0xe1,0x1c,0x6d,0xde,0xd1,0xc2]

Then enter `sub_400620` to get the final thoughts of this challenge and see the pseudocode. We see that's `XORing` the encry_flag with `the xor_key` and then `shifting right` with `1`. The xor_key comes from `(i % 0FF) | 0xA0`.

<p align="center">
  <img src="/cyberdefenders_re101/img/6.png" />
</p>
<br>

xor_hey = [0xa0,0xa1,0xa2,0xa3,0xa4,0xa5,0xa6,0xa7,0xa8,0xa9,0xaa,0xab,0xac,0xad,0xae,0xaf,0xb0,0xb1,0xb2,0xb3,0xb4,0xb5,0xb6,0xb7,0xb8,0xb9,0xba,0xbb,0xbc,0xbd,0xbe,0xbf].

I will use [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('0x%20with%20comma')XOR(%7B'option':'Hex','string':'0xa0,0xa1,0xa2,0xa3,0xa4,0xa5,0xa6,0xa7,0xa8,0xa9,0xaa,0xab,0xac,0xad,0xae,0xaf,0xb0,0xb1,0xb2,0xb3,0xb4,0xb5,0xb6,0xb7,0xb8,0xb9,0xba,0xbb,0xbc,0xbd,0xbe,0xbf'%7D,'Standard',false)OR(%7B'option':'Hex','string':'1'%7D)Bit_shift_right(1,'Logical%20shift')&input=MHg2ZCwweDc4LDB4NjEsMHg2YywweGRkLDB4N2UsMHg2NSwweDdlLDB4NDcsMHg2YSwweDRmLDB4Y2MsMHhmNywweGNhLDB4NzMsMHg2OCwweDU1LDB4NDIsMHg1MywweGRjLDB4ZDcsMHhkNCwweDZiLDB4ZWMsMHhkYiwweGQyLDB4ZTEsMHgxYywweDZkLDB4ZGUsMHhkMSwweGMy) to do this operation. Then the flag shows up.

<p align="center">
  <img src="/cyberdefenders_re101/img/7.png" />
</p>
<br>

> malwar3-3ncryp710n-15-Sh17

# Challenge quote

> Keyboard not found. Press any key to continue.
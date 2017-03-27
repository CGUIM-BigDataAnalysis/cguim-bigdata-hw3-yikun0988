長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
#這是R Code Chunk
library(rvest) ##第一次使用要先安裝 install.packages("rvest")
```

    ## Warning: package 'rvest' was built under R version 3.3.3

    ## Loading required package: xml2

    ## Warning: package 'xml2' was built under R version 3.3.3

``` r
for(i in 1:5){  ##一頁20筆，要跑5頁才有100筆
    PTTmovie <- paste("https://www.ptt.cc/bbs/movie/index",i,".html",sep="")
    Title <- read_html(PTTmovie, encoding = "UTF-8") %>% html_nodes(".title a") %>% html_text()
    PushNum <- read_html(PTTmovie, encoding = "UTF-8") %>% html_nodes(".nrec") %>% html_text()
    Author <- read_html(PTTmovie, encoding = "UTF-8") %>% html_nodes(".author") %>% html_text()
    if(i==1){
    a = data.frame(Title, PushNum, Author)
    }
    else if(i==2){
    b = data.frame(Title, PushNum, Author)
    }
    else if(i==3){
    c = data.frame(Title, PushNum, Author)
    }
    else if(i==4){
    d = data.frame(Title, PushNum, Author)
    }
    else {
    e = data.frame(Title, PushNum, Author)
    }
}
moivedata = rbind(a, b, c, d, e) ##整合5個data.frame
print(moivedata)
```

    ##                                                Title PushNum       Author
    ## 1                  [討論] 夏日童年--四眼田雞麥諾利多      27      IamJean
    ## 2                         [知識] 我又再看神鬼傳奇1了      67      demona.
    ## 3                          [心得] 昨天東森演的鬼上門       2        nin64
    ## 4                                [心得] 三部曲之鬥法       3      cyrille
    ## 5          [心得] 看完《女神陷阱》的碎碎唸..........       5       Comer.
    ## 6                           [心得] 情路長短調…有劇情       1      getlaw.
    ## 7                        [轉貼] alice看~「摩登」時代       3     bohemia.
    ## 8       [感想] 紅色,瘋狂,縱火的原點:Point of Origi …       2   totoroJack
    ## 9                              Re: [心得] 藍色協奏曲       1       loiter
    ## 10                           [心得] 我看<藍色協奏曲>       4       Jolynn
    ## 11                                 [心得] 第凡內早餐       2     cavinlai
    ## 12      [心得] Dark Fury: 星際傳奇跟超世紀戰警間遺 …           firewalker
    ## 13         [心得] Movie~魔女嘉麗--無法擺脫的校園悲劇              bushman
    ## 14                 [情報] "Flamenco" by Carlos Saura       1    TulipChiu
    ## 15                               [心得] 終極追殺令~~       6     yoyo9269
    ## 16                           [情報] 關於異形的小常識      12         A1an
    ## 17                       [閒聊] 終極戰士也是會進步的       5          bbc
    ## 18                         [心得] 剛看了大蟒蛇血蘭花      16      shinada
    ## 19                                [心得] 決戰時刻~~        9     yoyo9269
    ## 20                          Re:[心得] 美國殺人魔結局       6    EvilBunny
    ## 21                               Re: [閒聊] 十大禁片       8  MerinoSheep
    ## 22                   [心得] 最抽象的電影--"上帝轉身"       5      howwell
    ## 23           [心得] V字特攻隊 - 很西部的吸血鬼動作片      10   firewalker
    ## 24                         [討論] 啟示錄的討論(劇情)               md1011
    ## 25                     Re: [討論] 啟示錄的討論(劇情)                Xtaka
    ## 26                     Re: [討論] 啟示錄的討論(劇情)       1        cimes
    ## 27           [心得] 終極奇兵(The Thirteenth Warrior)       2     cavinlai
    ## 28              [心得] 蝙蝠俠 - 漫畫改編電影的大成功       4   firewalker
    ## 29     [心得] 蝙蝠俠2 - 波頓魔力再度讓黑暗籠罩高譚市       7   firewalker
    ## 30       [閒聊] 關於上面聊的 Robert De Niro 簽名一事      16   firewalker
    ## 31   Re: [閒聊] 關於上面聊的 Robert De Niro 簽名一事       1   firewalker
    ## 32      [心得] 鷹女 - 騎士+冒險+浪漫+魔法 的中古奇 …       3   firewalker
    ## 33                         [心得] 三更2-餃子(有劇情)       1       kensam
    ## 34                   [心得] Bang, Bang, You're Dead        1        asity
    ## 35             [心得]【蝙蝠俠三】 - 蝙蝠俠沒落的開始       4   firewalker
    ## 36                                 [心得] 妙麗的春宵      15       Chante
    ## 37                               [心得] 全球十大禁片      36      birdjay
    ## 38                     [心得] 看完鬼飯店(有一點劇情)       1  TheLastSong
    ## 39                 Re: [心得] 看完鬼飯店(有一點劇情)       3       hagdon
    ## 40                    [閒聊] 全球十大禁片-鳥杰回應篇       4      birdjay
    ## 41      [心得] Wonder Boys：幽默聰明的劇本，精采的 …       1   firewalker
    ## 42                                 [心得] 終極酷斯拉       7     cavinlai
    ## 43                       Re: [討論] 在雙眼的縫隙之間       1        molon
    ## 44              [影評] DVD -Scary Movie 3<驚聲尖笑3>       3       Mansun
    ## 45           [影評]《綠寶石》八○年代的浪漫冒險代表作           firewalker
    ## 46                [影評]《尼羅河寶石》走向不同的續集           firewalker
    ## 47                       [影評] 走進奇探心魔如入迷宮           filmwalker
    ## 48                             [心得] 這個男人有點色       1     cavinlai
    ## 49      [心得] 一吻可否化鴻溝:蘇格蘭之吻(Ae Fond K …       2   totoroJack
    ## 50           [情報] 英國影迷票選史上最遜的電影對白！      14        gless
    ## 51         [心得]【戰略高手】- Soderbergh 最酷的電影       3   firewalker
    ## 52                 [心得] 我心目中2004下半年十大佳片      14         holf
    ## 53                                   [影評] 異形系列       6     gonghang
    ## 54                   [心得] 2004年令我失望的十大電影      22         holf
    ## 55                               Re: [閒聊] 十大禁片      10         soga
    ## 56                [影評]《極幻迷樂之旅》與心碎的聲音               fansss
    ## 57                                   [心得] 紅色情深       3     cavinlai
    ## 58     [感想] 最強,新潮流,天下第一劍:名劍(the Sword)           totoroJack
    ## 59                    [心得]《樂士浮生錄2‧名揚四海》       3      sunline
    ## 60                                   [心得] 白色情迷       1     cavinlai
    ## 61                        [請益] 有人看過鬼頭鬼腦嗎?       2         Ucse
    ## 62        [感想] 莎岡,疏離,陸地上的魚:Jose與虎與魚們       1   totoroJack
    ## 63                             [推薦] 黑澤明的七武士       8       Leelmm
    ## 64                         [影評] 縱情慾海(restless)                keane
    ## 65                                   [感想] 太陽帝國       1   smallchiou
    ## 66                                   [心得] 北非諜影       2     cavinlai
    ## 67                                     [心得] 三更２       5       windxx
    ## 68        [影評] 古墓奇兵2 - 印第安納瓊斯+詹姆士龐德       2   firewalker
    ## 69               [心得] 昨晚看了一不老電影Funny Girl       4     windspir
    ## 70            [心得] 電影《大法師：吸魂首部曲》有感        1        fay88
    ## 71                  [心得] 電影《在黑暗中漫舞》有感        3        fay88
    ## 72                       [心得] Man bites Dog (1992)       2      adonkey
    ## 73      [影評] 匈奴王傳奇（阿提拉）/以人物為主的戰 …       2   firewalker
    ## 74            [影評] 1996麻雀變鳳凰 - 二見鐘情的翻版       1   firewalker
    ## 75                              [心得] 新北斗神拳OVA       4     cavinlai
    ## 76                 [心得] 縱情四海The Man Who Cried        2    establish
    ## 77                   [影評] 攻殼二：巴特的孤獨與溫柔       5       Stormy
    ## 78               Re: [影評] 攻殼二：巴特的孤獨與溫柔       2       hemels
    ## 79      [感想] 搖擺,爵士,請相信音樂:搖擺女孩(Swing …       6   totoroJack
    ## 80         [閒聊] "穿梭時空" 類型電影 自圓其說的方式      11   filmwalker
    ## 81                             [心得] 謎中謎 Charade       3   libraryfay
    ## 82                    [感想] Swing with Swing girls!       6   totoroJack
    ## 83              [影評] 不負責任影評：《Swing Girls》             jimulder
    ## 84                        [心得] 水瓶座女孩 (含劇情)       6        ycycv
    ## 85   Re: [問題] 教父2 為什麼麥可要把哥哥佛雷多殺了呢       8      autorad
    ## 86                             [心得] 希臘左巴（雷）       2     Muhchyng
    ## 87   Re: [問題] 教父2 為什麼麥可要把哥哥佛雷多殺了呢       6    smilelamb
    ## 88                        [心得] 夢幻天堂 (內有劇情)       5        Nekoi
    ## 89               [情報] 台灣與大陸的電影翻譯名稱比較      29        hu236
    ## 90           [影評] 黑人解救政府血淚史-<限制級戰警2>       3       Mansun
    ## 91          Re: [心得] Love the hard way!（有劇情喔)       5    justmyway
    ## 92                [影評] 遇見莉莉 從遵從到反叛的試探           filmwalker
    ## 93                            Re: [影評] 限制級戰警2       2       Stormy
    ## 94      [心得] 當哈利碰上莎莉 When Harry Met Sally         2  lovefriends
    ## 95      [感想] 低級,屎尿,我愛大美國:美國特警隊(Tea …           totoroJack
    ## 96        [影評]《星際大戰第三部曲：西斯大帝的復仇》       2   filmwalker
    ## 97  [影評] 不負責任影評：《星際大戰3西斯大帝的復仇》       4     jimulder
    ## 98                           [專題] 星戰電影課前溫習       5   filmwalker
    ## 99                       [ 雷 ] 帝國降臨：星戰三部曲       5       Stormy
    ## 100                      [心得] 關於星戰三的一點心得       3 a00000000926

``` r
##read_html
##html_nodes
##html_text
```

爬蟲結果呈現
------------

``` r
knitr::kable(moivedata[1:100,c("Title","PushNum","Author")])  ##請將iris取代為上個步驟中產生的爬蟲資料資料框
```

| Title                                              | PushNum | Author       |
|:---------------------------------------------------|:--------|:-------------|
| \[討論\] 夏日童年--四眼田雞麥諾利多                | 27      | IamJean      |
| \[知識\] 我又再看神鬼傳奇1了                       | 67      | demona.      |
| \[心得\] 昨天東森演的鬼上門                        | 2       | nin64        |
| \[心得\] 三部曲之鬥法                              | 3       | cyrille      |
| \[心得\] 看完《女神陷阱》的碎碎唸..........        | 5       | Comer.       |
| \[心得\] 情路長短調…有劇情                         | 1       | getlaw.      |
| \[轉貼\] alice看~「摩登」時代                      | 3       | bohemia.     |
| \[感想\] 紅色,瘋狂,縱火的原點:Point of Origi …     | 2       | totoroJack   |
| Re: \[心得\] 藍色協奏曲                            | 1       | loiter       |
| \[心得\] 我看<藍色協奏曲>                          | 4       | Jolynn       |
| \[心得\] 第凡內早餐                                | 2       | cavinlai     |
| \[心得\] Dark Fury: 星際傳奇跟超世紀戰警間遺 …     |         | firewalker   |
| \[心得\] Movie~魔女嘉麗--無法擺脫的校園悲劇        |         | bushman      |
| \[情報\] "Flamenco" by Carlos Saura                | 1       | TulipChiu    |
| \[心得\] 終極追殺令~~                              | 6       | yoyo9269     |
| \[情報\] 關於異形的小常識                          | 12      | A1an         |
| \[閒聊\] 終極戰士也是會進步的                      | 5       | bbc          |
| \[心得\] 剛看了大蟒蛇血蘭花                        | 16      | shinada      |
| \[心得\] 決戰時刻~~                                | 9       | yoyo9269     |
| Re:\[心得\] 美國殺人魔結局                         | 6       | EvilBunny    |
| Re: \[閒聊\] 十大禁片                              | 8       | MerinoSheep  |
| \[心得\] 最抽象的電影--"上帝轉身"                  | 5       | howwell      |
| \[心得\] V字特攻隊 - 很西部的吸血鬼動作片          | 10      | firewalker   |
| \[討論\] 啟示錄的討論(劇情)                        |         | md1011       |
| Re: \[討論\] 啟示錄的討論(劇情)                    |         | Xtaka        |
| Re: \[討論\] 啟示錄的討論(劇情)                    | 1       | cimes        |
| \[心得\] 終極奇兵(The Thirteenth Warrior)          | 2       | cavinlai     |
| \[心得\] 蝙蝠俠 - 漫畫改編電影的大成功             | 4       | firewalker   |
| \[心得\] 蝙蝠俠2 - 波頓魔力再度讓黑暗籠罩高譚市    | 7       | firewalker   |
| \[閒聊\] 關於上面聊的 Robert De Niro 簽名一事      | 16      | firewalker   |
| Re: \[閒聊\] 關於上面聊的 Robert De Niro 簽名一事  | 1       | firewalker   |
| \[心得\] 鷹女 - 騎士+冒險+浪漫+魔法 的中古奇 …     | 3       | firewalker   |
| \[心得\] 三更2-餃子(有劇情)                        | 1       | kensam       |
| \[心得\] Bang, Bang, You're Dead                   | 1       | asity        |
| \[心得\]【蝙蝠俠三】 - 蝙蝠俠沒落的開始            | 4       | firewalker   |
| \[心得\] 妙麗的春宵                                | 15      | Chante       |
| \[心得\] 全球十大禁片                              | 36      | birdjay      |
| \[心得\] 看完鬼飯店(有一點劇情)                    | 1       | TheLastSong  |
| Re: \[心得\] 看完鬼飯店(有一點劇情)                | 3       | hagdon       |
| \[閒聊\] 全球十大禁片-鳥杰回應篇                   | 4       | birdjay      |
| \[心得\] Wonder Boys：幽默聰明的劇本，精采的 …     | 1       | firewalker   |
| \[心得\] 終極酷斯拉                                | 7       | cavinlai     |
| Re: \[討論\] 在雙眼的縫隙之間                      | 1       | molon        |
| \[影評\] DVD -Scary Movie 3<驚聲尖笑3>             | 3       | Mansun       |
| \[影評\]《綠寶石》八○年代的浪漫冒險代表作          |         | firewalker   |
| \[影評\]《尼羅河寶石》走向不同的續集               |         | firewalker   |
| \[影評\] 走進奇探心魔如入迷宮                      |         | filmwalker   |
| \[心得\] 這個男人有點色                            | 1       | cavinlai     |
| \[心得\] 一吻可否化鴻溝:蘇格蘭之吻(Ae Fond K …     | 2       | totoroJack   |
| \[情報\] 英國影迷票選史上最遜的電影對白！          | 14      | gless        |
| \[心得\]【戰略高手】- Soderbergh 最酷的電影        | 3       | firewalker   |
| \[心得\] 我心目中2004下半年十大佳片                | 14      | holf         |
| \[影評\] 異形系列                                  | 6       | gonghang     |
| \[心得\] 2004年令我失望的十大電影                  | 22      | holf         |
| Re: \[閒聊\] 十大禁片                              | 10      | soga         |
| \[影評\]《極幻迷樂之旅》與心碎的聲音               |         | fansss       |
| \[心得\] 紅色情深                                  | 3       | cavinlai     |
| \[感想\] 最強,新潮流,天下第一劍:名劍(the Sword)    |         | totoroJack   |
| \[心得\]《樂士浮生錄2‧名揚四海》                   | 3       | sunline      |
| \[心得\] 白色情迷                                  | 1       | cavinlai     |
| \[請益\] 有人看過鬼頭鬼腦嗎?                       | 2       | Ucse         |
| \[感想\] 莎岡,疏離,陸地上的魚:Jose與虎與魚們       | 1       | totoroJack   |
| \[推薦\] 黑澤明的七武士                            | 8       | Leelmm       |
| \[影評\] 縱情慾海(restless)                        |         | keane        |
| \[感想\] 太陽帝國                                  | 1       | smallchiou   |
| \[心得\] 北非諜影                                  | 2       | cavinlai     |
| \[心得\] 三更２                                    | 5       | windxx       |
| \[影評\] 古墓奇兵2 - 印第安納瓊斯+詹姆士龐德       | 2       | firewalker   |
| \[心得\] 昨晚看了一不老電影Funny Girl              | 4       | windspir     |
| \[心得\] 電影《大法師：吸魂首部曲》有感            | 1       | fay88        |
| \[心得\] 電影《在黑暗中漫舞》有感                  | 3       | fay88        |
| \[心得\] Man bites Dog (1992)                      | 2       | adonkey      |
| \[影評\] 匈奴王傳奇（阿提拉）/以人物為主的戰 …     | 2       | firewalker   |
| \[影評\] 1996麻雀變鳳凰 - 二見鐘情的翻版           | 1       | firewalker   |
| \[心得\] 新北斗神拳OVA                             | 4       | cavinlai     |
| \[心得\] 縱情四海The Man Who Cried                 | 2       | establish    |
| \[影評\] 攻殼二：巴特的孤獨與溫柔                  | 5       | Stormy       |
| Re: \[影評\] 攻殼二：巴特的孤獨與溫柔              | 2       | hemels       |
| \[感想\] 搖擺,爵士,請相信音樂:搖擺女孩(Swing …     | 6       | totoroJack   |
| \[閒聊\] "穿梭時空" 類型電影 自圓其說的方式        | 11      | filmwalker   |
| \[心得\] 謎中謎 Charade                            | 3       | libraryfay   |
| \[感想\] Swing with Swing girls!                   | 6       | totoroJack   |
| \[影評\] 不負責任影評：《Swing Girls》             |         | jimulder     |
| \[心得\] 水瓶座女孩 (含劇情)                       | 6       | ycycv        |
| Re: \[問題\] 教父2 為什麼麥可要把哥哥佛雷多殺了呢  | 8       | autorad      |
| \[心得\] 希臘左巴（雷）                            | 2       | Muhchyng     |
| Re: \[問題\] 教父2 為什麼麥可要把哥哥佛雷多殺了呢  | 6       | smilelamb    |
| \[心得\] 夢幻天堂 (內有劇情)                       | 5       | Nekoi        |
| \[情報\] 台灣與大陸的電影翻譯名稱比較              | 29      | hu236        |
| \[影評\] 黑人解救政府血淚史-<限制級戰警2>          | 3       | Mansun       |
| Re: \[心得\] Love the hard way!（有劇情喔)         | 5       | justmyway    |
| \[影評\] 遇見莉莉 從遵從到反叛的試探               |         | filmwalker   |
| Re: \[影評\] 限制級戰警2                           | 2       | Stormy       |
| \[心得\] 當哈利碰上莎莉 When Harry Met Sally       | 2       | lovefriends  |
| \[感想\] 低級,屎尿,我愛大美國:美國特警隊(Tea …     |         | totoroJack   |
| \[影評\]《星際大戰第三部曲：西斯大帝的復仇》       | 2       | filmwalker   |
| \[影評\] 不負責任影評：《星際大戰3西斯大帝的復仇》 | 4       | jimulder     |
| \[專題\] 星戰電影課前溫習                          | 5       | filmwalker   |
| \[ 雷 \] 帝國降臨：星戰三部曲                      | 5       | Stormy       |
| \[心得\] 關於星戰三的一點心得                      | 3       | a00000000926 |

解釋爬蟲結果
------------

``` r
str(moivedata)
```

    ## 'data.frame':    100 obs. of  3 variables:
    ##  $ Title  : Factor w/ 97 levels "[心得] Dark Fury: 星際傳奇跟超世紀戰警間遺 …",..: 13 12 6 3 7 9 18 17 19 4 ...
    ##  $ PushNum: Factor w/ 21 levels "","1","12","16",..: 6 11 5 7 9 2 7 5 2 8 ...
    ##  $ Author : Factor w/ 61 levels "A1an","bbc","bohemia.",..: 12 8 15 7 6 11 3 17 14 13 ...

解釋解釋解釋解釋: str()用途廣泛，在我想了解一筆資料時或未知變數的時候，就是使用它的時候，str()顯示資料結構，列出資料內每個欄位的狀態，以上就使用str()列出了moivedata中有100筆觀察值，有5個變項，其中level為自訂義，代表每遇到一個不同的文章標題都會有一個新的level產生，所以這裡有97個不同的文章標題，21個不同的推文數，以及61個不同的作者。

``` r
table(moivedata $ Author)
```

    ## 
    ##         A1an          bbc     bohemia.      bushman     cavinlai 
    ##            1            1            1            1            8 
    ##       Comer.      cyrille      demona.    EvilBunny   firewalker 
    ##            1            1            1            1           15 
    ##      getlaw.      IamJean       Jolynn       loiter        nin64 
    ##            1            1            1            1            1 
    ##      shinada   totoroJack    TulipChiu     yoyo9269        asity 
    ##            1            7            1            2            1 
    ##      birdjay       Chante        cimes       hagdon      howwell 
    ##            2            1            1            1            1 
    ##       kensam       md1011  MerinoSheep  TheLastSong        Xtaka 
    ##            1            1            1            1            1 
    ##       fansss   filmwalker        gless     gonghang         holf 
    ##            1            5            1            1            2 
    ##       Mansun        molon         soga      sunline      adonkey 
    ##            2            1            1            1            1 
    ##    establish        fay88       hemels        keane       Leelmm 
    ##            1            2            1            1            1 
    ##   smallchiou       Stormy         Ucse     windspir       windxx 
    ##            1            3            1            1            1 
    ## a00000000926      autorad        hu236     jimulder    justmyway 
    ##            1            1            1            2            1 
    ##   libraryfay  lovefriends     Muhchyng        Nekoi    smilelamb 
    ##            1            1            1            1            1 
    ##        ycycv 
    ##            1

``` r
sort(table(moivedata$Author),decreasing=TRUE)[1:5]
```

    ## 
    ## firewalker   cavinlai totoroJack filmwalker     Stormy 
    ##         15          8          7          5          3

解釋解釋解釋解釋: table()能彙整factor、list、data frame中分類組合發生次數，table(moivedata $ Author)把moivedata中的Author欄位每個作者的發文數給計算出來，我們可以看到firewalker在前100篇文章中就發了15篇文章。

人工結論與解釋解釋解釋解釋解釋解釋解釋: 在頁面部分的網址部分，因為ptt的網址一頁一頁有規律性，差別只在於index後面的數字，所以換頁不是什麼大困難，再來因為需要100筆資料，所以我總共搜尋了5頁，在分析的時候我們發現firewalker在前100篇文章中就發了15篇文章，firewalker可能平時很閒，或是他像是板主一樣在照顧電影版，所以在前5頁的100篇文章中就發了15篇文章，應該是一個發文狂人或是電影愛好者，再來我利用sort()把前5筆次數高的作者給顯示出來，發現還有一位filmwalker，我推測它有可能是firewalker的粉絲或朋友，也可能根本就是分身帳號。

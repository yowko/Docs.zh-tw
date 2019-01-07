---
title: 規則運算式語言 - 快速參考
ms.date: 03/30/2017
ms.technology: dotnet-standard
f1_keywords:
- VS.RegularExpressionBuilder
helpviewer_keywords:
- regex cheat sheet
- parsing text with regular expressions, language elements
- searching with regular expressions, language elements
- pattern-matching with regular expressions, language elements
- regular expressions, language elements
- regular expressions [.NET Framework]
- cheat sheet
- .NET Framework regular expressions, language elements
ms.assetid: 930653a6-95d2-4697-9d5a-52d11bb6fd4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09f2886173bd3a80691b78a6e3ea71b034ebe34a
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54030395"
---
# <a name="regular-expression-language---quick-reference"></a>規則運算式語言 - 快速參考
<a name="top"></a>規則運算式是規則運算式引擎嘗試在輸入文字中比對的模式。 模式是由一個或多個字元常值、運算子或建構所組成。  如需簡介，請參閱 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)。  
  
 本快速參考的每一節列出您可以用於定義規則運算式的特定某類字元、運算子和建構：  
  
 [逸出字元](#character_escapes)  
 [字元類別](#character_classes)  
 [錨點](#anchors)  
 [群組建構](#grouping_constructs)  
 [數量詞](#quantifiers)  
 [反向參考建構](#backreference_constructs)  
 [替代建構](#alternation_constructs)  
 [替代](#substitutions)  
 [規則運算式選項](#options)  
 [其他建構](#miscellaneous_constructs)  
  
 我們也有用兩種格式提供此資訊，可讓您下載及列印，以方便參考。  
  
 [以 Word (.docx) 格式下載](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [下載 PDF (.pdf) 格式](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
<a name="character_escapes"></a>   
## <a name="character-escapes"></a>逸出字元  
 規則運算式中的反斜線字元 (\\) 表示接在後面的字元是特殊字元 (如下表所示)，或應該解譯為常值。 如需詳細資訊，請參閱[逸出字元](../../../docs/standard/base-types/character-escapes-in-regular-expressions.md)。  
  
|逸出的字元|說明|模式|符合|  
|-----------------------|-----------------|-------------|-------------|  
|`\a`|比對警示字元 \u0007。|`\a`|"Error!" 中的 "\u0007" + '\u0007'|  
|`\b`|在字元類別中，比對退格鍵 \u0008。|`[\b]{3,}`|"\b\b\b\b" 中的 "\b\b\b\b"|  
|`\t`|比對定位點 \u0009。|`(\w+)\t`|"item1\titem2\t" 中的 "item1\t"、"item2\t"|  
|`\r`|比對歸位字元 \u000D (`\r` 不等於新行字元 `\n`。)|`\r\n(\w+)`|"\r\nThese are\ntwo lines." 中的 "\r\nThese"|  
|`\v`|比對垂直定位點 \u000B。|`[\v]{2,}`|"\v\v\v" 中的 "\v\v\v"|  
|`\f`|比對換頁字元 \u000C。|`[\f]{2,}`|"\f\f\f" 中的 "\f\f\f"|  
|`\n`|比對新行字元 \u000A。|`\r\n(\w+)`|"\r\nThese are\ntwo lines." 中的 "\r\nThese"|  
|`\e`|比對逸出字元 \u001B。|`\e`|"\x001B" 中的 "\x001B"|  
|`\` *nnn*|使用八進位表示法指定字元 (*nnn* 由兩位數或三位數組成)。|`\w\040\w`|"a b", "c d" in<br /><br /> "a bc d"|  
|`\x` *nn*|使用十六進位表示指定字元 (*nn* 由剛好兩位數組成)。|`\w\x20\w`|"a b", "c d" in<br /><br /> "a bc d"|  
|`\c` *X*<br /><br /> `\c` *x*|比對 *X* 或 *x*所指定的 ASCII 控制字元，其中 *X* 或 *x* 是控制字元的字母。|`\cC`|"\x0003" (Ctrl-C) 中的 "\x0003"|  
|`\u` *nnnn*|使用十六進位表示比對 Unicode 字元 (剛好四位數，如 *nnnn*所表示)。|`\w\u0020\w`|"a b", "c d" in<br /><br /> "a bc d"|  
|`\`|當後面加上的字元不是這張表和本主題其他表格中指出的逸出字元時，則比對該字元。 例如， `\*` 與 `\x2A`相同，而 `\.` 與 `\x2E`相同。 這可讓規則運算式引擎釐清語言元素 (例如 \* 或 ?) 和字元常值 (以 `\*` 或 `\?` 表示)。|`\d+[\+-x\*]\d+`|"(2+2) \* 3\*9" 中的 "2+2" 和 "3\*9"|  
  
 [回到頁首](#top)  
  
<a name="character_classes"></a>   
## <a name="character-classes"></a>字元類別  
 字元類別會比對一組字元中的任何一個字元。 字元類別包含下表列出的語言項目。 如需詳細資訊，請參閱 [Character Classes](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。  
  
|字元類別|說明|模式|符合|  
|---------------------|-----------------|-------------|-------------|  
|`[` *character_group* `]`|比對 *character_group*中的任何單一字元。 根據預設，比對會區分大小寫。|`[ae]`|"gray" 中的 "a"<br /><br /> "lane" 中的 "a"、"e"|  
|`[^` *character_group* `]`|否定：比對不在 *character_group* 中的任何單一字元。 根據預設， *character_group* 中的字元會區分大小寫。|`[^aei]`|"reign" 中的 "r"、"g"、"n"|  
|`[` *第一* `-` *last* `]`|字元範圍：比對從 *first* 至 *last* 範圍內的任何單一字元。|`[A-Z]`|"AB123" 中的 "A"、"B"|  
|`.`|萬用字元：比對除 \n 以外的任何單一字元。<br /><br /> 若要比對常值句號字元 (. 或 `\u002E`)，您必須在前面加上逸出字元 (`\.`)。|`a.e`|"nave" 中的 "ave"<br /><br /> "water" 中的 "ate"|  
|`\p{` *name* `}`|比對 Unicode 一般分類中或 *name*指定之具名區塊中的任何單一字元。|`\p{Lu}`<br /><br /> `\p{IsCyrillic}`|"City Lights" 中的 "C"、"L"<br /><br /> "ДЖem" 中的 "Д"、"Ж"|  
|`\P{` *name* `}`|比對不在 Unicode 一般分類中或 *name*所指定之具名區塊中的任何單一字元。|`\P{Lu}`<br /><br /> `\P{IsCyrillic}`|"City" 中的 "i"、"t"、"y"<br /><br /> "ДЖem" 中的 "e"、"m"|  
|`\w`|比對任何文字字元。|`\w`|"ID A1.3" 中的 "I"、"D"、"A"、"1"、"3"|  
|`\W`|比對任何非文字字元。|`\W`|"ID A1.3" 中的 " "、"."|  
|`\s`|比對任何泛空白字元。|`\w\s`|"ID A1.3" 中的 "D "|  
|`\S`|比對任何非泛空白字元。|`\s\S`|"int \__ctr" 中的 " _"|  
|`\d`|比對任何十進位數字。|`\d`|"4 = IV" 中的 "4"|  
|`\D`|比對十進位數字以外的任何字元。|`\D`|"4 = IV" 中的 " "、"="、" "、"I"、"V"|  
  
 [回到頁首](#top)  
  
## <a name="anchors"></a>錨點  
 錨點 (即原子零寬度判斷提示) 會造成根據字串中的目前位置來決定比對成功或失敗，但不會造成引擎在字串中前進或是取用字元。 下表列出的 metacharacter 是錨點。 如需詳細資訊，請參閱 [錨點](../../../docs/standard/base-types/anchors-in-regular-expressions.md)。  
  
|判斷提示|說明|模式|符合|  
|---------------|-----------------|-------------|-------------|  
|`^`|根據預設，比對必須在字串的開頭開始；在多行模式中，它必須在一行的開頭開始。|`^\d{3}`|"901-" 中的<br /><br /> "901-333-"|  
|`$`|根據預設，比對必須發生在字串的結尾或字串結尾的 `\n` 之前；在多行模式中，它必須發生在一行的結尾之前，或一行結尾的 `\n` 之前。|`-\d{3}$`|"-333" 中的<br /><br /> "-901-333"|  
|`\A`|比對必須發生在字串開頭。|`\A\d{3}`|"901-" 中的<br /><br /> "901-333-"|  
|`\Z`|比對必須發生在字串結尾，或發生在字串結尾的 `\n` 之前。|`-\d{3}\Z`|"-333" 中的<br /><br /> "-901-333"|  
|`\z`|比對必須發生在字串結尾。|`-\d{3}\z`|"-333" 中的<br /><br /> "-901-333"|  
|`\G`|比對必須發生在先前比對結束的位置。|`\G\(\d\)`|"(1)(3)(5)[7](9\)" 中的 "(1)"、"(3)"、"(5)"|  
|`\b`|比對必須發生在 `\w` (英數) 和 `\W` (非英數) 字元之間的界限上。|`\b\w+\s\w+\b`|"them theme them them" 中的 "them theme"、"them them"|  
|`\B`|比對不可以發生在 `\b` 界限上。|`\Bend\w*\b`|"end sends endure lender" 中的 "ends"、"ender"|  
  
 [回到頁首](#top)  
  
<a name="grouping_constructs"></a>   
## <a name="grouping-constructs"></a>群組建構  
 群組建構會描寫規則運算式的子運算式，而且通常會擷取輸入字串的子字串。 群組建構包含下表列出的語言項目。 如需詳細資訊，請參閱 [Grouping Constructs](grouping-constructs-in-regular-expressions.md)。  
  
|群組建構|說明|模式|符合|  
|------------------------|-----------------|-------------|-------------|  
|`(` *子運算式* `)`|擷取符合的子運算式，並指派以一為起始的序號給它。|`(\w)\1`|"deep" 中的 "ee"|  
|`(?<` *name* `>` *子運算式* `)`|將符合的子運算式擷取到具名群組中。|`(?<double>\w)\k<double>`|"deep" 中的 "ee"|  
|`(?<` *名稱1* `-` *名稱2* `>` *子運算式* `)`|定義對稱群組定義。 如需詳細資訊，請參閱 [Grouping Constructs](grouping-constructs-in-regular-expressions.md)中的＜對稱群組定義＞一節。|`(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$`|"3+2^((1-3)\*(3-1))" 中的 "((1-3)\*(3-1))"|  
|`(?:` *子運算式* `)`|定義非擷取型群組。|`Write(?:Line)?`|"Console.WriteLine()" 中的 "WriteLine"<br /><br /> "Console.Write(value)" 中的 "Write"|  
|`(?imnsx-imnsx:` *子運算式* `)`|套用或停用 *subexpression*內指定的選項。 如需詳細資訊，請參閱 [Regular Expression Options](regular-expression-options.md)。|`A\d{2}(?i:\w+)\b`|"A12xl A12XL a12xl" 中的 "A12xl"、"A12XL"|  
|`(?=` *子運算式* `)`|零寬度右合樣 (Positive Lookahead) 判斷提示。|`\w+(?=\.)`|"He is. The dog ran. The sun is out." 中的 "is"、"ran" 和 "out"|  
|`(?!` *子運算式* `)`|零寬度右不合樣 (Negative Lookahead) 判斷提示。|`\b(?!un)\w+\b`|"unsure sure unity used" 中的 "sure"、"used"|  
|`(?<=` *子運算式* `)`|零寬度左合樣 (Positive Lookbehind) 判斷提示。|`(?<=19)\d{2}\b`|"1851 1999 1950 1905 2003" 中的 "99"、"50"、"05"|  
|`(?<!` *子運算式* `)`|零寬度左不合樣 (Negative Lookbehind) 判斷提示。|`(?<!19)\d{2}\b`|"1851 1999 1950 1905 2003" 中的 "51"、"03"|  
|`(?>` *子運算式* `)`|非回溯子運算式，也稱為窮盡 (Greedy) 子運算式。|`[13579](?>A+B+)`|"1ABB 3ABBC 5AB 5AC" 中的 "1ABB"、"3ABB" 和 "5AB"|  
  
 [回到頁首](#top)  
  
<a name="quantifiers"></a>   
## <a name="quantifiers"></a>數量詞  
 數量詞指定上一個項目 (可能是字元、群組或字元類別) 必須在輸入字串中出現多少次，才算符合。 數量詞包含下表列出的語言項目。 如需詳細資訊，請參閱 [Quantifiers](quantifiers-in-regular-expressions.md)。  
  
|數量詞|說明|模式|符合|  
|----------------|-----------------|-------------|-------------|  
|`*`|比對上一個項目零次或多次。|`\d*\.\d`|".0"、"19.9"、"219.9"|  
|`+`|比對上一個項目一次或多次。|`"be+"`|"been" 中的 "bee"、"bent" 中的 "be"|  
|`?`|比對上一個項目零次或一次。|`"rai?n"`|"ran"、"rain"|  
|`{` *n* `}`|比對上一個項目剛好 *n* 次。|`",\d{3}"`|"1,043.6" 中的 ",043"、"9,876,543,210" 中的 ",876"、",543" 和 ",210"|  
|`{` *n* `,}`|比對上一個項目至少 *n* 次。|`"\d{2,}"`|"166"、"29"、"1930"|  
|`{` *n* `,` *m* `}`|比對上一個項目至少 *n* 次，但不超過 *m* 次。|`"\d{3,5}"`|"166"、"17668"<br /><br /> "193024" 中的 "19302"|  
|`*?`|比對上一個項目零次以上，但越少次越好。|`\d*?\.\d`|".0"、"19.9"、"219.9"|  
|`+?`|比對上一個項目一次或多次，但越少次越好。|`"be+?"`|"been" 中的 "be"、"bent" 中的 "be"|  
|`??`|比對上一個項目零次或一次，但越少次越好。|`"rai??n"`|"ran"、"rain"|  
|`{` *n* `}?`|比對前一個項目剛好 *n* 次。|`",\d{3}?"`|"1,043.6" 中的 ",043"、"9,876,543,210" 中的 ",876"、",543" 和 ",210"|  
|`{` *n* `,}?`|比對前一個項目至少 *n* 次，但愈少次愈好。|`"\d{2,}?"`|"166"、"29"、"1930"|  
|`{` *n* `,` *m* `}?`|比對前一個項目 *n* 次到 *m* 次，但越少次越好。|`"\d{3,5}?"`|"166"、"17668"<br /><br /> "193024" 中的 "193"、"024"|  
  
 [回到頁首](#top)  
  
<a name="backreference_constructs"></a>   
## <a name="backreference-constructs"></a>反向參考建構  
 反向參考可於後來在相同規則運算式中再識別先前符合的子運算式。 下表列出 .NET 中規則運算式所支援的反向參考建構。 如需詳細資訊，請參閱 [Backreference Constructs](backreference-constructs-in-regular-expressions.md)。  
  
|反向參考建構|說明|模式|符合|  
|-----------------------------|-----------------|-------------|-------------|  
|`\` *數字*|反向參考。 比對編號子運算式的值。|`(\w)\1`|"seek" 中的 "ee"|  
|`\k<` *name* `>`|命名的反向參考。 比對具名運算式的值。|`(?<char>\w)\k<char>`|"seek" 中的 "ee"|  
  
 [回到頁首](#top)  
  
<a name="alternation_constructs"></a>   
## <a name="alternation-constructs"></a>交替建構  
 交替建構會修改規則運算式來啟用二選一比對。 這些建構包含下表列出的語言項目。 如需詳細資訊，請參閱 [Alternation Constructs](alternation-constructs-in-regular-expressions.md)。  
  
|交替建構|說明|模式|符合|  
|---------------------------|-----------------|-------------|-------------|  
|<code>&#124;</code>|比對由分隔號 (&#124;) 字元所隔開的任何一個元素。|<code>th(e&#124;is&#124;at)</code>|後面這個字串中的 "the"、"this"："this is the day. "|  
|`(?(` *expression* `)` *yes* <code>&#124;</code> *no* `)`|如果 *expression* 所指定的規則運算式模式相符，則比對 *yes* ，否則比對選擇性的 *no* 部分。 *expression* 會解譯為零寬度判斷提示。|<code>(?(A)A\d{2}\b&#124;\b\d{3}\b)</code>|"A10 C103 910" 中的 "A10"、"910"|  
|`(?(` *name* `)` *yes* <code>&#124;</code> *no* `)`|如果 *name* (具名或編號擷取群組) 有相符項目，則比對 *yes*，否則比對選擇性的 *no*。|<code>(?&lt;quoted&gt;&quot;)?(?(quoted).+?&quot;&#124;\S+\s)</code>|"Dogs.jpg "Yiska playing.jpg"" 中的 Dogs.jpg、"Yiska playing.jpg"|  
  
 [回到頁首](#top)  
  
<a name="substitutions"></a>   
## <a name="substitutions"></a>替代  
 替代是取代模式中支援的規則運算式語言項目。 如需詳細資訊，請參閱 [Substitutions](substitutions-in-regular-expressions.md)。 下表列出的 metacharacter 是原子零寬度判斷提示。  
  
|字元|說明|模式|取代模式|輸入字串|結果字串|  
|---------------|-----------------|-------------|-------------------------|------------------|-------------------|  
|`$` number|替代群組 *number*所比對的子字串。|`\b(\w+)(\s)(\w+)\b`|`$3$2$1`|"one two"|"two one"|  
|`${` *name* `}`|替代具名群組 *name*所比對的子字串。|`\b(?<word1>\w+)(\s)(?<word2>\w+)\b`|`${word2} ${word1}`|"one two"|"two one"|  
|`$$`|替代常值 "$"。|`\b(\d+)\s?USD`|`$$$1`|"103 USD"|"$103"|  
|`$&`|替代整個符合項目的複本。|`\$?\d*\.?\d+`|`**$&**`|"$1.30"|"\*\*$1.30\*\*"|  
|``$` ``|替代輸入字串中符合字串前面的所有文字。|`B+`|``$` ``|"AABBCC"|"AAAACC"|  
|`$'`|替代輸入字串中符合字串後面的所有文字。|`B+`|`$'`|"AABBCC"|"AACCCC"|  
|`$+`|替代已擷取的最後一個群組。|`B+(C+)`|`$+`|"AABBCCDD"|"AACCDD"|  
|`$_`|替代整個輸入字串。|`B+`|`$_`|"AABBCC"|"AAAABBCCCC"|  
  
 [回到頁首](#top)  
  
<a name="options"></a>   
## <a name="regular-expression-options"></a>規則運算式選項  
 您可以指定選項，以控制規則運算式引擎如何解譯規則運算式模式。 這些選項中有許多可以指定為內嵌 (在規則運算式模式中) 或是一個或多個 <xref:System.Text.RegularExpressions.RegexOptions> 常數。 這個快速參考只列出內嵌選項。 如需內嵌和 <xref:System.Text.RegularExpressions.RegexOptions> 選項的詳細資訊，請參閱 [Regular Expression Options](regular-expression-options.md)。  
  
 您可以透過兩種方式指定內嵌選項：  
  
-   使用 [其他建構](miscellaneous-constructs-in-regular-expressions.md) `(?imnsx-imnsx)`，其中選項或選項集合前面的減號 (-) 會關閉這些選項。 例如， `(?i-mn)` 會開啟不區分大小寫的比對 (`i`)、關閉多行模式 (`m`)，以及關閉未命名的群組擷取 (`n`)。 選項會從定義該選項的位置開始套用至規則運算式模式並且保持生效，直到模式結尾或出現另一個建構反轉選項為止。  
  
-   使用 [grouping construct](grouping-constructs-in-regular-expressions.md)`(?imnsx-imnsx:`*子運算式*`)`，只針對指定的群組定義選項。  
  
 .NET 規則運算式引擎支援下列內嵌選項。  
  
|選項|說明|模式|符合|  
|------------|-----------------|-------------|-------------|  
|`i`|使用不區分大小寫的比對方式。|`\b(?i)a(?-i)a\w+\b`|"aardvark AAAuto aaaAuto Adam breakfast" 中的 "aardvark"、"aaaAuto"|  
|`m`|使用多行模式。 `^` 和 `$` 符合行的開頭與結尾，而不是字串的開始和結尾。|如需範例，請參閱 [Regular Expression Options](regular-expression-options.md)中的＜多行模式＞一節。||  
|`n`|不擷取未命名的群組。|如需範例，請參閱 [Regular Expression Options](regular-expression-options.md)中的＜僅明確擷取＞一節。||  
|`s`|使用單行模式。|如需範例，請參閱 [Regular Expression Options](regular-expression-options.md)中的＜單行模式＞一節。||  
|`x`|忽略規則運算式模式中未逸出的空白字元。|`\b(?x) \d+ \s \w+`|"1 aardvark 2 cats IV centurions" 中的 "1 aardvark"、"2 cats"|  
  
 [回到頁首](#top)  
  
<a name="miscellaneous_constructs"></a>   
## <a name="miscellaneous-constructs"></a>其他建構  
 其他建構會修改規則運算式模式或提供其相關資訊。 下表列出 .NET 所支援的其他建構。 如需詳細資訊，請參閱 [Miscellaneous Constructs](miscellaneous-constructs-in-regular-expressions.md)。  
  
|建構|定義|範例|  
|---------------|----------------|-------------|  
|`(?imnsx-imnsx)`|在模式中間設定或停用選項，例如不區分大小寫。如需詳細資訊，請參閱[規則運算式選項](regular-expression-options.md)。|`\bA(?i)b\w+\b` 會比對 "ABA Able Act" 中的 "ABA"、"Able"|  
|`(?#` *註解* `)`|內嵌註解。 註解會在第一個右括號結束。|`\bA(?#Matches words starting with A)\w+\b`|  
|`#` [至行尾]|X 模式註解。 註解從未逸出的 `#` 開始，並延續到行尾。|`(?x)\bA\w+\b#Matches words starting with A`|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex>  
- [規則運算式](regular-expressions.md)  
- [規則運算式類別](the-regular-expression-object-model.md)  
- [規則運算式範例](regular-expression-examples.md)  
- [規則運算式 - 快速參考 (以 Word 格式下載)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [規則運算式 - 快速參考 (以 PDF 格式下載)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

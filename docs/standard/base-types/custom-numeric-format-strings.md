---
title: 自訂數值格式字串
ms.date: 06/25/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- format strings
- custom numeric format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- formatting numbers [.NET Framework]
- format specifiers, custom numeric format strings
ms.assetid: 6f74fd32-6c6b-48ed-8241-3c2b86dea5f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab06c2d87de9483d7a3e9eb810f4be1f3278ddc2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64634528"
---
# <a name="custom-numeric-format-strings"></a>自訂數值格式字串

您可以建立由一個或多個自訂數值規範所組成的自訂數值格式字串，以定義如何格式化數值資料。 自訂數值格式字串為任何非 [標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)的格式字串。  

 所有數字類型的 `ToString` 方法的一些多載可支援自訂數值格式字串。 例如，您可以提供數值格式字串給 <xref:System.Int32.ToString%28System.String%29> 類型的 <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29> 和 <xref:System.Int32> 方法。 .NET 的[複合格式功能](../../../docs/standard/base-types/composite-formatting.md)也支援自訂數值格式字串，此功能會由 <xref:System.Console> 與 <xref:System.IO.StreamWriter> 類別的一些 `Write` 和 `WriteLine` 方法，以及 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法和 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> 方法所使用。 [字串內插補點](../../csharp/language-reference/tokens/interpolated.md)功能也支援自訂數值格式字串。  
  
> [!TIP]
>  您可以下載 [格式化公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)，這個應用程式可讓您將格式字串套用至數值或日期和時間值，並且顯示結果字串。  
  
<a name="table"></a> 下表說明自訂數值格式規範，並顯示每個格式範例所產生的範例輸出。 如需使用自訂數值格式字串的詳細資訊，請參閱 [注意](#NotesCustomFormatting) 一節，如需其用法的完整解說，請參閱 [範例](#example) 一節。  
  
|格式規範|名稱|說明|範例|  
|----------------------|----------|-----------------|--------------|  
|"0"|零值預留位置|以對應的數字 (如果有的話) 取代零，否則結果字串中會出現零。<br /><br /> 詳細資訊：["0" 自訂規範](#Specifier0)。|1234.5678 ("00000") -> 01235<br /><br /> 0.45678 ("0.00", en-US) -> 0.46<br /><br /> 0.45678 ("0.00", fr-FR) -> 0,46|  
|"#"|數字預留位置|將 "#" 符號取代為對應的數字 (如果有的話)，否則結果字串中不會出現任何數字。<br /><br /> 請注意，如果輸入字串中對應的數字是不重要的 0，結果字串中就不會顯示任何數字。 例如，0003 ("####") -> 3。<br /><br /> 詳細資訊：["#" 自訂規範](#SpecifierD)。|1234.5678 ("#####") -> 1235<br /><br /> 0.45678 ("#.##", en-US) -> .46<br /><br /> 0.45678 ("#.##", fr-FR) -> ,46|  
|"."|小數點|決定結果字串中小數點的位置。<br /><br /> 詳細資訊：["."自訂規範](#SpecifierPt)。|0.45678 ("0.00", en-US) -> 0.46<br /><br /> 0.45678 ("0.00", fr-FR) -> 0,46|  
|","|群組分隔符號和數值範圍|同時做為群組分隔符號和數值縮放規範。 如果做為群組分隔符號，則會在每個群組之間插入當地語系化群組分隔符號字元。 做為數值縮放規範時，每指定一個逗號就會將數字除以 1000。<br /><br /> 詳細資訊：["," 自訂規範](#SpecifierTh)。|群組分隔符號規範：<br /><br /> 2147483647 ("##,#", en-US) -> 2,147,483,647<br /><br /> 2147483647 ("##,#", es-ES) -> 2.147.483.647<br /><br /> 縮放規範：<br /><br /> 2147483647 ("#,#,,", en-US) -> 2,147<br /><br /> 2147483647 ("#,#,,", es-ES) -> 2.147|  
|"%"|百分比預留位置|將數字乘以 100，並在結果字串中插入當地語系化的百分比符號。<br /><br /> 詳細資訊：["%" 自訂規範](#SpecifierPct)。|0.3697 ("%#0.00", en-US) -> %36.97<br /><br /> 0.3697 ("%#0.00", el-GR) -> %36,97<br /><br /> 0.3697 ("##.0 %", en-US) -> 37.0 %<br /><br /> 0.3697 ("##.0 %", el-GR) -> 37,0 %|  
|"‰"|千分之一符號預留位置|將數字乘以 1000，並在結果字串中插入當地語系化的千分比符號。<br /><br /> 詳細資訊：["‰" 自訂規範](#SpecifierPerMille)。|0.03697 ("#0.00‰", en-US) -> 36.97‰<br /><br /> 0.03697 ("#0.00‰", ru-RU) -> 36,97‰|  
|"E0"<br /><br /> "E+0"<br /><br /> "E-0"<br /><br /> "E0"<br /><br /> "E+0"<br /><br /> "E-0"|指數標記法|如果後面至少接著一個 0 (零)，則使用指數標記法來格式化結果。 大小寫 "E" 或 "e" 表示結果字串中指數符號的大小寫。 接在 "E" 或 "e" 字元後面的零個數決定指數中的最少位數。 加號 (+) 表示指數前面一律加上正負號字元。 減號 (-) 表示只在負指數前面才加上正負號字元。<br /><br /> 詳細資訊：["E" 和 "e" 自訂規範](#SpecifierExponent)。|987654 ("#0.0e0") -> 98.8e4<br /><br /> 1503.92311 ("0.0##e+00") -> 1.504e+03<br /><br /> 1.8901385E-16 ("0.0e+00") -> 1.9e-16|  
|"\\"|逸出字元|將下一個字元解譯為常值，而不是自訂格式規範。<br /><br /> 詳細資訊：["\\" 逸出字元](#SpecifierEscape)。|987654 ("\\###00\\#") -> #987654#|  
|'*string*'<br /><br /> "*字串*"|常值字串分隔符號|表示應該將所括住的字元原封不動地複製到結果字串。<br/><br/>詳細資訊：[字元常值](#character-literals)。|68 ("# 'degrees'") -> 68 degrees<br /><br /> 68 ("# ' degrees'") -> 68  degrees|  
|;|區段分隔符號|以個別格式字串來定義正數、負數和零值的區段。<br /><br /> 詳細資訊：[";" 區段分隔符號](#SectionSeparator)。|12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#);-\0-") -> -0-<br /><br /> -12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)<br /><br /> 12.345 ("#0.0#;(#0.0#)") -> 12.35<br /><br /> 0 ("#0.0#;(#0.0#)") -> 0.0<br /><br /> -12.345 ("#0.0#;(#0.0#)") -> (12.35)|  
|其他|所有其他字元|字元會原封不動地複製到結果字串。<br/><br/>詳細資訊：[字元常值](#character-literals)。|68 ("# °") -> 68 °|  
  
 下列各節提供每個自訂數值格式規範的詳細資訊。  

[!INCLUDE[C# interactive-note](~/includes/csharp-interactive-partial-note.md)] 
  
<a name="Specifier0"></a>   
## <a name="the-0-custom-specifier"></a>"0" 自訂規範  
 "0" 自訂格式規範是當做零預留位置符號。 如果正在格式化的值有數字位於格式字串中出現零的位置上，則該數字會複製到結果字串，否則結果字串中會出現零。 小數點前最左邊的零和小數點後最右邊的零位置，決定要一直在輸出字串中出現的位數範圍。  
  
 "00" 規範會造成數值捨入至最接近的小數點前面數值，而其中永遠使用遠離零的捨入方式。 例如，使用 "00" 格式化 34.5 將會得到值 35。  
  
 下列範例顯示使用包含零預留位置的自訂格式字串來格式化的幾個值。  
  
 [!code-cpp[Formatting.Numeric.Custom#1](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#1)]
 [!code-csharp[Formatting.Numeric.Custom#1](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#1)]
 [!code-vb[Formatting.Numeric.Custom#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#1)]  
  
 [回到表格](#table)  
  
<a name="SpecifierD"></a>   
## <a name="the--custom-specifier"></a>"#" 自訂規範  
 "#" 自訂格式規範是當做數字預留位置符號。 如果正在格式化的值有數字位於格式字串中出現 "#" 符號的位置上，則該數字會複製到輸出字串。 否則，沒有東西會存放在結果字串中的那個位置。  
  
 請注意，這個規範永遠不會顯示不是有效位數的零，即使字串中只有零這個數字也一樣。 只有當零在所顯示的數字中是有效位數時，才會顯示零。  
  
 "##" 格式字串會造成數值捨入至最接近的小數點前面數值，而其中永遠使用遠離零的捨入方式。 例如，使用 "##" 格式化 34.5 將會得到值 35。  
  
 下列範例顯示使用包含數字預留位置的自訂格式字串來格式化的幾個值。  
  
 [!code-cpp[Formatting.Numeric.Custom#2](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#2)]
 [!code-csharp[Formatting.Numeric.Custom#2](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#2)]
 [!code-vb[Formatting.Numeric.Custom#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#2)]  
  
 若要傳回結果字串，以空格取代不存在的數字或前置零，請使用 [複合格式功能](../../../docs/standard/base-types/composite-formatting.md) 並指定欄位寬度，如下列範例所示。  
  
 [!code-cpp[Formatting.Numeric.Custom#12](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/SpaceOrDigit1.cpp#12)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#12](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/SpaceOrDigit1.cs#12)]
 [!code-vb[Formatting.Numeric.Custom#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/SpaceOrDigit1.vb#12)]  
  
 [回到表格](#table)  
  
<a name="SpecifierPt"></a>   
## <a name="the--custom-specifier"></a>"." 自訂規範  
 "." 自訂格式規範會將當地語系化的十進位分隔符號插入結果字串中。 格式字串中第一個點決定所格式化值中的小數分隔符號位置；任何其他點將被忽略。  
  
 結果字串中當做小數分隔符號的字元不一定是點，而是由控制格式設定的 <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> 物件的 <xref:System.Globalization.NumberFormatInfo> 屬性來決定。  
  
 下列範例使用 "." 格式規範來定義幾個結果字串中小數點的位置。  
  
 [!code-cpp[Formatting.Numeric.Custom#3](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#3)]
 [!code-csharp[Formatting.Numeric.Custom#3](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#3)]
 [!code-vb[Formatting.Numeric.Custom#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#3)]  
  
 [回到表格](#table)  
  
<a name="SpecifierTh"></a>   
## <a name="the--custom-specifier"></a>"," 自訂規範  
 "," 字元同時當做群組分隔符號和數值縮放規範。  
  
- 群組分隔符號：如果在用於格式化數字整數位數的兩個數字預留位置 (0 或 #) 之間指定一或多個逗號，則會在輸出的整數部分中在每個數字群組之間插入群組分隔符號字元。  
  
     目前 <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A> 物件的 <xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A> 和 <xref:System.Globalization.NumberFormatInfo> 屬性會判斷當做數字群組分隔符號使用的字元，以及每個數字群組的大小。 例如，如果使用字串 "#,#" 和不變的文化特性來格式化數字 1000，則輸出為 "1,000"。  
  
- 數值縮放規範：如果在明確或隱含小數點的左側緊接著指定一或多個逗號，則每指定一個逗號就會將要格式化的數字除以 1000。 例如，如果使用字串 "0,," 來格式化數字 1 億，則其輸出為 "100"。  
  
 您可以在相同的格式字串內使用群組分隔符號和數值縮放規範。 例如，如果使用字串 "#,0,," 和不變的文化特性來格式化數字 10 億，則輸出為 "1,000"。  
  
 下列範例示範使用逗號做為群組分隔符號。  
  
 [!code-cpp[Formatting.Numeric.Custom#4](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#4)]
 [!code-csharp[Formatting.Numeric.Custom#4](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#4)]
 [!code-vb[Formatting.Numeric.Custom#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#4)]  
  
 下列範例示範使用逗點做為數值縮放的規範。  
  
 [!code-cpp[Formatting.Numeric.Custom#5](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#5)]
 [!code-csharp[Formatting.Numeric.Custom#5](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#5)]
 [!code-vb[Formatting.Numeric.Custom#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#5)]  
  
 [回到表格](#table)  
  
<a name="SpecifierPct"></a>   
## <a name="the--custom-specifier"></a>"%" 自訂規範  
 格式字串中的百分比符號 (%) 會使得數字在格式化之前先乘以 100。 數字中會根據格式字串中出現 % 的位置，插入當地語系化百分比符號。 使用的百分比字元由目前 <xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A> 物件的 <xref:System.Globalization.NumberFormatInfo> 屬性所定義。  
  
 下列範例會定義幾個包含 "%" 自訂規範的自訂格式字串。  
  
 [!code-cpp[Formatting.Numeric.Custom#6](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#6)]
 [!code-csharp[Formatting.Numeric.Custom#6](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#6)]
 [!code-vb[Formatting.Numeric.Custom#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#6)]  
  
 [回到表格](#table)  
  
<a name="SpecifierPerMille"></a>   
## <a name="the--custom-specifier"></a>"‰" 自訂規範  
 格式字串中的千分比字元 (‰ 或 \u2030) 會使得數字在格式化之前先乘以 1000。 傳回的字串中會根據格式字串中出現 ‰ 符號的位置，插入適當的千分比符號。 使用的千分之一符號字元是由提供文化特性特定格式資訊之物件的 <xref:System.Globalization.NumberFormatInfo.PerMilleSymbol%2A?displayProperty=nameWithType> 屬性定義的。  
  
 下列範例會定義包含 "‰" 自訂規範的自訂格式字串。  
  
 [!code-cpp[Formatting.Numeric.Custom#9](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#9)]
 [!code-csharp[Formatting.Numeric.Custom#9](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#9)]
 [!code-vb[Formatting.Numeric.Custom#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#9)]  
  
 [回到表格](#table)  
  
<a name="SpecifierExponent"></a>   
## <a name="the-e-and-e-custom-specifiers"></a>"E" 和 "e" 自訂規範  
 如果 "E"、"E+"、"E-"、"e"、"e+" 或 "e-" 中的任何一個字串出現在格式字串中，且後面至少緊接著一個零，則會使用科學標記法來格式化數字，並在數字和指數之間插入 "E" 或 "e"。 接在科學標記法指標之後的零個數決定要在指數部分輸出的最少位數。 "E+" 和 "e+" 格式表示指數前面應該一律加上加號或減號。 "E"、"E-"、"e" 或 "e-" 格式表示只應該在負數指數前面加上正負號字元。  
  
 下列範例使用科學記號規範來格式化幾個數值。  
  
 [!code-cpp[Formatting.Numeric.Custom#7](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#7)]
 [!code-csharp[Formatting.Numeric.Custom#7](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#7)]
 [!code-vb[Formatting.Numeric.Custom#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#7)]  
  
 [回到表格](#table)  
  
<a name="SpecifierEscape"></a>   
## <a name="the--escape-character"></a>"\\" 逸出字元  
 格式字串中的 "#"、"0"、"."、","、"%" 和 "‰" 符號會解譯為格式規範，而不是常值字元。 大寫和小寫 "E" 以及 + 和 - 符號視其在自訂格式字串中的位置而定，也有可能會解譯為格式規範。  
  
 若要避免將字元解譯為格式規範，您可以在前面加上反斜線，這是逸出字元。 逸出字元表示接下來的字元是字元常值，應該原封不動地放入結果字串中。  
  
 若要在結果字串中加上反斜線，您必須再加上一個反斜線 (變成`\\`)，才能將反斜線解譯為常值。  
  
> [!NOTE]
>  某些編譯器 (例如 C++ 和 C# 編譯器) 也可能會將單一反斜線字元解譯為逸出字元。 為了確保字串在格式化時能夠正確獲得解譯，您可以在 C# 中的字串前面加上逐字字串常值字元 (@ 字元)，或在 C# 和 C++ 中的每個反斜線前面再加上一個反斜線字元。 下列 C# 範例示範這兩種做法。  
  
 下列範例會使用逸出字元，以避免格式化作業將 "#"、"0" 和 "\\" 字元解譯為逸出字元或格式規範。 C# 範例會多使用一個反斜線，以確保反斜線會解譯為常值字元。  
  
 [!code-cpp[Formatting.Numeric.Custom#11](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/escape1.cpp#11)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#11](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/escape1.cs#11)]
 [!code-vb[Formatting.Numeric.Custom#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/escape1.vb#11)]  
  
 [回到表格](#table)  
  
<a name="SectionSeparator"></a>   
## <a name="the--section-separator"></a>";" 區段分隔符號  
 冒號 (;) 是條件式格式規範，這個規範會根據數字的值是正數、負數還是零，將不同的格式套用至數字。 若要產生這個行為，自訂格式字串可以包含多達三個以分號分隔的區段， 下表將說明這些區段。  
  
|區段數|說明|  
|------------------------|-----------------|  
|一個區段|此格式字串適用於所有的值。|  
|兩個區段|第一個區段適用於正數值及零值，第二個區段適用於負數值。<br /><br /> 如果要格式化的數字為負數，但依照第二個區段的格式四捨五入之後成為零，則產生的零會依照第一個區段來格式化。|  
|三個區段|第一個區段適用於正數值，第二個區段適用於負數值，而第三個區段則適用於零值。<br /><br /> 第二個區段可留白 (分號之間沒有任何內容)，此時第一個區段將套用到所有非零值。<br /><br /> 如果要格式化的數字不是零，但依照第一個或第二個區段的格式四捨五入之後成為零，則產生的零會依照第三個區段來格式化。|  
  
 區段分隔符號會在最終值已格式化時，忽略任何事先存在而與數值相關的格式。 例如，負數值在使用區段分隔符號時永遠不以負號來顯示。 如果您想要最終的格式化值具有負號，您應該明確包含負號做為自訂格式規範的一部分。  
  
 下列範例會使用 ";" 格式規範，以不同方式格式化正數、負數和零。  
  
 [!code-cpp[Formatting.Numeric.Custom#8](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/custom.cpp#8)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#8](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/custom.cs#8)]
 [!code-vb[Formatting.Numeric.Custom#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/Custom.vb#8)]  
  
 [回到表格](#table)  

## <a name="character-literals"></a>字元常值  
 
自訂數值格式字串中出現的格式規範一律會解譯為格式字元，永遠不會解譯為常值字元。 這包含下列字元：  

- [0](#Specifier0)
- [\#](#SpecifierD)
- [%](#SpecifierPct)
- [‰](#SpecifierPerMille)
- '
- [\\](#SpecifierEscape)
- [.](#SpecifierPt)
- [、](#SpecifierTh)
- [E 或 e](#SpecifierExponent)，取決於在格式字串中的位置。

所有其他字元一律會解譯為字元常值，並在格式化作業中，原封不動地包含在結果字串中。  在剖析作業中，它們必須完全符合輸入字串中的字元；這項比較會區分大小寫。  
  
下列範例說明常值字元單位 (在此案例中為千分位) 的一個常見用法：
  
 [!code-csharp-interactive[literal characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal2.cs#1)]
 [!code-vb[literal characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal2.vb#1)]  
  
 您可以使用兩種方式來指定將字元解譯為常值字元，而不是格式字元，以便包含在結果字串中，或在輸入字串中成功剖析：  
  
- 逸出格式字元。 如需詳細資訊，請參閱 ["\\" 逸出字元](#SpecifierEscape)。
  
- 以引號括住整個常值字串。

下列範例會使用這兩種方法，在自訂數值格式字串中包含保留的字元。  
  
 [!code-csharp-interactive[including reserved characters](~/samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/literal1.cs#1)]
 [!code-vb[including reserved characters](~/samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/literal1.vb#1)]  
    
<a name="NotesCustomFormatting"></a>   
## <a name="notes"></a>注意  
  
### <a name="floating-point-infinities-and-nan"></a>無限浮點數和 NaN  
 不論格式字串為何，如果 <xref:System.Single> 或 <xref:System.Double> 浮點類型的值為正無限大、負無限大或不是數字 (NaN)，則格式化後的字串會分別是 <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A>、 <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>或 <xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A> 屬性的值 (這些屬性由目前適用的 <xref:System.Globalization.NumberFormatInfo> 物件所指定)。  
  
### <a name="control-panel-settings"></a>控制台設定  
 [控制台] 中 [ **地區及語言選項]** 項目的設定會影響格式化作業所產生的結果字串。 這些設定是用來初始化與目前執行緒文化特性相關聯的 <xref:System.Globalization.NumberFormatInfo> 物件，而且目前的執行緒文化特性會提供用來管理格式的值。 使用不同設定的電腦會產生不同的結果字串。  
  
 此外，如果您使用 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType> 建構函式來具現化新的 <xref:System.Globalization.CultureInfo> 物件，而此物件代表的文化特性與目前系統文化特性相同，則 [控制台] 中的 [ **地區及語言選項** ] 項目所建立的任何自訂都會套用至新的 <xref:System.Globalization.CultureInfo> 物件。 您可以使用 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來建立不反映系統自訂的 <xref:System.Globalization.CultureInfo> 物件。  
  
### <a name="rounding-and-fixed-point-format-strings"></a>四捨五入和定點格式字串  
 如果是定點格式字串 (即不含科學標記法格式字元的格式字串)，則數字會四捨五入成與小數點右邊之數字預留位置一樣多的小數位數。 如果格式字串不包含小數點，數值四捨五入至最接近的整數。 如果數值有比小數點左邊的數字預留位置還要多的位數，額外位數會緊接第一個數字預留位置之前複製到輸出字串。  
  
 [回到表格](#table)  
  
<a name="example"></a>   
## <a name="example"></a>範例  
 下列範例示範兩個自訂數值格式字串。 在這兩個範例中，數字預留位置 (`#`) 會顯示數值資料，而所有其他字元則會複製到結果字串中。  
  
 [!code-cpp[Formatting.Numeric.Custom#10](../../../samples/snippets/cpp/VS_Snippets_CLR/formatting.numeric.custom/cpp/example1.cpp#10)]
 [!code-csharp-interactive[Formatting.Numeric.Custom#10](../../../samples/snippets/csharp/VS_Snippets_CLR/formatting.numeric.custom/cs/example1.cs#10)]
 [!code-vb[Formatting.Numeric.Custom#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/formatting.numeric.custom/vb/example1.vb#10)]  
  
 [回到表格](#table)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>
- [格式化類型](../../../docs/standard/base-types/formatting-types.md)
- [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [如何：以前置字元零來填補數字](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)
- [範例：.NET Framework 4 格式化公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)

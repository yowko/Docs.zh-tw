---
title: 作法：確認字串是否為有效的電子郵件格式
ms.date: 12/10/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- email [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6381747bc998f73b374442fcb15e025ca15795d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589532"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>作法：確認字串是否為有效的電子郵件格式
下列範例會使用規則運算式來確認字串是否為有效的電子郵件格式。  

## <a name="example"></a>範例  
 此範例會定義 `IsValidEmail` 方法，如果字串包含有效的電子郵件地址，則這個方法會傳回 `true` ，否則會傳回 `false` ，但不會採取其他任何動作。  
  
 為了驗證電子郵件地址是否有效， `IsValidEmail` 方法會以 <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> 規則運算式模式呼叫 `(@)(.+)$` 方法，從電子郵件地址分離出網域名稱。 第三個參數是 <xref:System.Text.RegularExpressions.MatchEvaluator> 委派，用於表示處理並取代相符文字的方法。 規則運算式模式解譯如下。  
  
|模式|說明|  
|-------------|-----------------|  
|`(@)`|比對 @ 字元。 這是第一個擷取群組。|  
|`(.+)`|比對出現一次或多次的任何字元。 這是第二個擷取群組。|  
|`$`|在字串的結尾結束比對。|  
  
 網域名稱會連同 @ 字元一併傳遞至 `DomainMapper` 方法，該方法會使用 <xref:System.Globalization.IdnMapping> 類別將 US-ASCII 字元範圍以外的 Unicode 字元轉譯為 Punycode。 如果 `invalid` 方法在網域名稱中偵測到任何無效字元，則方法也會將 `True` 旗標設定為 <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> 。 方法會將前面加上 @ 符號的 Punycode 網域名稱傳回至 `IsValidEmail` 方法。  
  
 接著 `IsValidEmail` 方法會呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> 方法，確認位址符合規則運算式模式。  
  
 請注意， `IsValidEmail` 方法並不會驗證電子郵件地址的真實性。 它只會判斷電子郵件地址的格式是否有效。 此外， `IsValidEmail` 方法不會驗證最上層網域名稱是否為 [IANA 根區域資料庫](https://www.iana.org/domains/root/db)列出的有效網域名稱，這項驗證需要執行查閱作業。 規則運算式只會驗證最上層網域名稱是否包含介於 2 到 24 個英數 ASCII 字元，且第一個和最後一個為英數字元，而其餘字元為英數字元或連字號 (-)。  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 在這個範例中，規則運算式模式 ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` 會依下表所示的方式解譯。 請注意，規則運算式是使用 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> 旗標所編譯。  
  
|模式|說明|  
|-------------|-----------------|  
|`^`|在字串開頭開始比對。|  
|`(?(")`|判斷第一個字元是否為引號。 `(?(")` 是交替建構的開頭。|  
|`(?("")("".+?(?<!\\)""@)`|如果第一個字元是引號，則比對是否為開頭引號後面至少接著一個任何字元，然後再接著結尾引號。 結尾引號前面絕不能是反斜線字元 (\\) 。 `(?<!` 是零寬度左不合樣 (Negative Lookbehind) 判斷提示的開頭。 此字串應該以 @ 記號做為結束。|  
|<code>&#124;(([0-9a-z]</code>|如果第一個字元不是引號，則比對 a 到 z 或 A 到 Z 的任何字母字元 (此比較不區分大小寫) 或 0 到 9 的任何數字字元。|  
|`(\.(?!\.))`|如果下一個字元是句號，則相符。 如果不是句號，則向右合樣下一個字元並繼續比對。 `(?!\.)` 是零寬度的右不合樣 (Negative Lookahead) 判斷提示，可防止電子郵件地址的本機部分出現兩個連續的句號。|  
|<code>&#124;[-!#\$%&'\*\+/=\?\^\`{}&#124;~\w]</code>|如果下一個字元不是句號，則比對任何文字字元或下列其中一個字元：-!#$%'*+=?^\`{}&#124;~。|  
|<code>((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^\`{}&#124;~\w])*</code>|比對交替模式 (句號後面接著非句號，或某個字元) 零次以上。|  
|`@`|比對 @ 字元。|  
|`(?<=[0-9a-z])`|如果位於 @ 字元前面的字元是 A 到 Z、a 到 z 或 0 到 9，則繼續比對。 `(?<=[0-9a-z])` 建構可定義零寬度的左合樣 (Positive Lookbehind) 判斷提示。|  
|`(?(\[)`|檢查 @ 後面的字元是否為左括號。|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|如果是左括號，則比對左括號後面是否接著 IP 位址 (四組 1 至 3 位數的數字，而每組數字均以句號隔開) 與右括號。|  
|<code>&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+</code>|如果 @ 後面的字元不是左括號，則比對一個值為 A-Z、a-z 或 0-9 的英數字元，該英數字元後面接著零或多個連字號，再接著值為 A-Z、a-z 或 0-9 的零或一個英數字元，最後接著句點。 此模式可以重複一或多次，且後面必須接最上層網域名稱。|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|最上層網域名稱必須以英數字元 (a-z、A-Z 和 0-9) 開頭和結尾。 其中也可以包含零到 22 個 ASCII 字元，英數字元或連字號皆可。|  
|`$`|在字串的結尾結束比對。|  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 `IsValidEmail` 和 `DomainMapper` 方法可以包含在規則運算式公用程式方法的程式庫中，或是做為私用的靜態或執行個體方法包含在應用程式類別中。  
  
 您也可以使用 <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> 方法，將此規則運算式包含在規則運算式程式庫中。  
  
 如果它們是在規則運算式程式庫中使用，則可以使用像是下列程式碼呼叫它們：  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
## <a name="see-also"></a>另請參閱

- [.NET Framework 規則運算式](../../../docs/standard/base-types/regular-expressions.md)

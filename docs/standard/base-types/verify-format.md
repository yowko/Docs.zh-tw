---
title: "如何：確認字串是否為有效的電子郵件格式"
description: "如何確認字串是否為有效的電子郵件格式"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6d735520-4059-4754-b34c-d117299d36f1
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 077a09152ac23c986a751f42c893e1dcca858291
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>如何：確認字串是否為有效的電子郵件格式

下列範例會使用規則運算式來確認字串是否為有效的電子郵件格式。

## <a name="example"></a>範例

此範例會定義 `IsValidEmail` 方法，如果字串包含有效的電子郵件地址，則這個方法會傳回 `true`，否則會傳回 `false`，但不會採取其他任何動作。 

為了確認電子郵件地址是否有效，`IsValidEmail` 方法會以 `(@)(.+)$` 規則運算式模式呼叫 [Regex.Replace(String, String, MatchEvaluator)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.Text.RegularExpressions.MatchEvaluator)) 方法，從電子郵件地址分離出網域名稱。 第三個參數是 [MatchEvaluator](xref:System.Text.RegularExpressions.MatchEvaluator) 委派，用於表示處理並取代相符文字的方法。 規則運算式模式解譯如下。 

模式 | 描述
------- | ----------- 
`(@)` | 比對 @ 字元。 這是第一個擷取群組。
`(.+)` | 比對出現一次或多次的任何字元。 這是第二個擷取群組。
`$` | 在字串的結尾結束比對。
 
網域名稱會連同 @ 字元一併傳遞至 `DomainMapper` 方法，該方法會使用 [IdnMapping](xref:System.Globalization.IdnMapping) 類別將 US-ASCII 字元範圍以外的 Unicode 字元轉譯為 Punycode。 如果 [IdnMapping.GetAscii](xref:System.Globalization.IdnMapping.GetAscii(System.String)) 方法在網域名稱中偵測到任何無效字元，則方法也會將 `invalid` 旗標設定為 `true`。 方法會將前面加上 @ 符號的 Punycode 網域名稱傳回至 `IsValidEmail` 方法。 

接著 `IsValidEmail` 方法會呼叫 [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) 方法，確認位址符合規則運算式模式。 

請注意，`IsValidEmail` 方法並不會驗證電子郵件地址的真實性。 它只會判斷電子郵件地址的格式是否有效。 此外，`IsValidEmail` 方法不會驗證最上層網域名稱是否為 [IANA 根區域資料庫](https://www.iana.org/domains/root/db)列出的有效網域名稱，這項驗證需要執行查閱作業。 規則運算式只會驗證最上層網域名稱是否包含介於&2; 到&24; 個英數 ASCII 字元，且第一個和最後一個為英數字元，而其餘字元為英數字元或連字號 (-)。 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class RegexUtilities
{
   bool invalid = false;

   public bool IsValidEmail(string strIn)
   {
       invalid = false;
       if (String.IsNullOrEmpty(strIn))
          return false;

       // Use IdnMapping class to convert Unicode domain names.
       try {
          strIn = Regex.Replace(strIn, @"(@)(.+)$", this.DomainMapper,
                                RegexOptions.None, TimeSpan.FromMilliseconds(200));
       }
       catch (RegexMatchTimeoutException) {
         return false;
       }

        if (invalid)
           return false;

       // Return true if strIn is in valid e-mail format.
       try {
          return Regex.IsMatch(strIn,
                @"^(?("")("".+?(?<!\\)""@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))" +
                @"(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$",
                RegexOptions.IgnoreCase, TimeSpan.FromMilliseconds(250));
       }
       catch (RegexMatchTimeoutException) {
          return false;
       }
   }

   private string DomainMapper(Match match)
   {
      // IdnMapping class with default property values.
      IdnMapping idn = new IdnMapping();

      string domainName = match.Groups[2].Value;
      try {
         domainName = idn.GetAscii(domainName);
      }
      catch (ArgumentException) {
         invalid = true;
      }
      return match.Groups[1].Value + domainName;
   }
}
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Class RegexUtilities
   Dim invalid As Boolean = False

   public Function IsValidEmail(strIn As String) As Boolean
       invalid = False
       If String.IsNullOrEmpty(strIn) Then Return False

       ' Use IdnMapping class to convert Unicode domain names.
       Try
          strIn = Regex.Replace(strIn, "(@)(.+)$", AddressOf Me.DomainMapper, 
                                RegexOptions.None, TimeSpan.FromMilliseconds(200))
       Catch e As RegexMatchTimeoutException
          Return False
       End Try

       If invalid Then Return False

       ' Return true if strIn is in valid e-mail format.
       Try
          Return Regex.IsMatch(strIn,
                 "^(?("")("".+?(?<!\\)""@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))" +
                 "(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$",
                 RegexOptions.IgnoreCase, TimeSpan.FromMilliseconds(250))
       Catch e As RegexMatchTimeoutException
          Return False
       End Try  
   End Function

   Private Function DomainMapper(match As Match) As String
      ' IdnMapping class with default property values.
      Dim idn As New IdnMapping()

      Dim domainName As String = match.Groups(2).Value
      Try
         domainName = idn.GetAscii(domainName)
      Catch e As ArgumentException
         invalid = True      
      End Try      
      Return match.Groups(1).Value + domainName
   End Function
End Class
```

在這個範例中，規則運算式模式 `^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^` \{ \} \|~ \w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z] [-\w]*[0-9a-z] *\.) [-a-za-z0-9] + [\-a-z0-9]{0,22}[a-z0-9]))$` 會依下表中所示的方式解譯。 請注意，規則運算式是使用 [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase) 旗標所編譯。

模式 | 描述
------- | ----------- 
`^` | 在字串開頭開始比對。
`(?(")` | 判斷第一個字元是否為引號。 `(?(")` 是替代建構的開頭。
`(?("")("".+?(?<!\\)""@)` | 如果第一個字元是引號，則比對是否為開頭引號後面至少接著一個任何字元，然後再接著結尾引號。 結尾引號前面絕不能是字元 `(\). (?<!`。 此字串應該以 @ 記號做為結束。
`&#124;(([0-9a-z] | 如果第一個字元不是引號，則比對 a 到 z 或 A 到 Z 的任何字母字元 (此比較不區分大小寫) 或 0 到 9 的任何數字字元。
`(\.(?!\.))` | 如果下一個字元是句號，則相符。 如果不是句號，則向右合樣下一個字元並繼續比對。 `(?!\.)` 是零寬度的右不合樣 (Negative Lookahead) 判斷提示，可防止電子郵件地址的本機部分出現兩個連續的句號。
`&#124;[-!#\$%&'\*\+/=\?\^`\{\}\&#124;~\w] | 如果下一個字元不是句號，則比對任何文字字元或下列其中一個字元：-!#$%'*+=?^`{}&#124;~。 
`((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`\{\}\&#124;~\w])* | 比對替代模式 (句號後面接著非句號，或某個字元) 零次以上。
`@` | 比對 @ 字元。
`(?<=[0-9a-z])` | 如果位於 @ 字元前面的字元是 A 到 Z、a 到 z 或 0 到 9，則繼續比對。 `(?<=[0-9a-z])` 建構可定義零寬度的左合樣 (Positive Lookbehind) 判斷提示。
`(?(\[)` | 檢查 @ 後面的字元是否為左括號。
`(\[(\d{1,3}\.){3}\d{1,3}\])` | 如果是左括號，則比對左括號後面是否接著 IP 位址 (四組&1; 至&3; 位數的數字，而每組數字均以句號隔開) 與右括號。
`&#124;(([0-9a-z][-\w]*[0-9a-z]*\.)+` | 如果 @ 後面的字元不是左括號，則比對一個值為 A-Z、a-z 或 0-9 的字母字元，該字母字元後面接著零個或多個文字字元或連字號，再接著值為 A-Z、a-z 或 0-9 的零個或一個英數字元，最後接著句號。 此模式可以重複一或多次，且後面必須接最上層網域名稱。 
`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` | 最上層網域名稱必須以英數字元 (a-z、A-Z 和 0-9) 開頭和結尾。 其中也可以包含零到 22 個 ASCII 字元，英數字元或連字號皆可。 
`$` | 在字串的結尾結束比對。
 
您可以使用下列這類程式碼來呼叫 `IsValidEmail` 和 `DomainMapper` 方法︰

```csharp
public class Application
{
   public static void Main()
   {
      RegexUtilities util = new RegexUtilities();
      string[] emailAddresses = { "david.jones@proseware.com", "d.j@server1.proseware.com",
                                  "jones@ms1.proseware.com", "j.@server1.proseware.com",
                                  "j@proseware.com9", "js#internal@proseware.com",
                                  "j_9@[129.126.118.1]", "j..s@proseware.com",
                                  "js*@proseware.com", "js@proseware..com",
                                  "js@proseware.com9", "j.s@server1.proseware.com",
                                   "\"j\\\"s\\\"\"@proseware.com", "js@contoso.中国" };

      foreach (var emailAddress in emailAddresses) {
         if (util.IsValidEmail(emailAddress))
            Console.WriteLine("Valid: {0}", emailAddress);
         else
            Console.WriteLine("Invalid: {0}", emailAddress);
      }                                            
   }
}
// The example displays the following output:
//       Valid: david.jones@proseware.com
//       Valid: d.j@server1.proseware.com
//       Valid: jones@ms1.proseware.com
//       Invalid: j.@server1.proseware.com
//       Valid: j@proseware.com9
//       Valid: js#internal@proseware.com
//       Valid: j_9@[129.126.118.1]
//       Invalid: j..s@proseware.com
//       Invalid: js*@proseware.com
//       Invalid: js@proseware..com
//       Valid: js@proseware.com9
//       Valid: j.s@server1.proseware.com
//       Valid: "j\"s\""@proseware.com
//       Valid: js@contoso.ä¸­å›½
```

```vb
Public Class Application
   Public Shared Sub Main()
      Dim util As New RegexUtilities()
      Dim emailAddresses() As String = { "david.jones@proseware.com", "d.j@server1.proseware.com", _
                                         "jones@ms1.proseware.com", "j.@server1.proseware.com", _
                                         "j@proseware.com9", "js#internal@proseware.com", _
                                         "j_9@[129.126.118.1]", "j..s@proseware.com", _
                                         "js*@proseware.com", "js@proseware..com", _
                                         "js@proseware.com9", "j.s@server1.proseware.com",
                                         """j\""s\""""@proseware.com", "js@contoso.中国" }

      For Each emailAddress As String In emailAddresses
         If util.IsValidEmail(emailAddress) Then
            Console.WriteLine("Valid: {0}", emailAddress)
         Else
            Console.WriteLine("Invalid: {0}", emailAddress)
         End If      
      Next                                            
   End Sub
End Class
' The example displays the following output:
'       Valid: david.jones@proseware.com
'       Valid: d.j@server1.proseware.com
'       Valid: jones@ms1.proseware.com
'       Invalid: j.@server1.proseware.com
'       Valid: j@proseware.com9
'       Valid: js#internal@proseware.com
'       Valid: j_9@[129.126.118.1]
'       Invalid: j..s@proseware.com
'       Invalid: js*@proseware.com
'       Invalid: js@proseware..com
'       Valid: js@proseware.com9
'       Valid: j.s@server1.proseware.com
'       Valid: "j\"s\""@proseware.com
'       Valid: js@contoso.ä¸­å›½
```

## <a name="see-also"></a>另請參閱

[.NET 規則運算式](regular-expressions.md)

[規則運算式範例](regex-examples.md)


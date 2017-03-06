---
title: "規則運算式的最佳做法"
description: "規則運算式的最佳做法"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 096fd614-91bf-4296-be24-12f62b062294
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: cf9c83de791fa4990a991689a26d4bbdd84cfe7d
ms.lasthandoff: 03/02/2017

---

# <a name="best-practices-for-regular-expressions"></a>規則運算式的最佳做法

.NET 中的規則運算式引擎是一項強大而功能完整的工具，會依據模式比對而非比較與比對常值文字的方式處理文字。 在大部分情況下，它會快速且有效率地執行模式比對。 不過，在某些情況下，規則運算式引擎速度可能變得相當慢。 而只有鮮少情況下，它甚至可能在處理相對小的輸入卻耗費數小時甚至數天時停止回應。 

本主題說明一些開發人員可以採用的最佳做法，確保其規則運算式達到最佳效能。 它包含以下各節：

* [考慮輸入來源](#consider-the-input-source)

* [適當處理物件具現化](#handle-object-instantiation-appropriately)

* [控制回溯](#take-charge-of-backtracking)

* [使用逾時值](#use-time-out-values)

* [必要時擷取](#capture-only-when-necessary)

* [相關主題](#related-topics)

## <a name="consider-the-input-source"></a>考慮輸入來源

一般而言，規則運算式可以接受兩種類型的輸入：受限制或未受限制。 受限制的輸入是來自已知或可靠來源，並且遵循預先定義格式的文字。 未受限制的輸入是來自不可靠來源 (例如 Web 使用者) 的文字，且可能未依循預先定義或預期的格式。

通常撰寫規則運算式模式的目的在於比對有效輸入。 也就是說，開發人員會檢查要比對的文字，然後撰寫比對該文字的規則運算式模式。 接著開發人員會利用多個有效的輸入項目進行測試，藉此判斷此模式是否需要更正或進一步詳述。 當模式符合所有假設的有效輸入時，即宣告準備好實際執行，並且可以納入已發行的應用程式中。 這種方式使得規則運算式模式相當適合比對限制的輸入， 不過卻不適合比對未受限制的輸入。

若要比對未受限制的輸入，規則運算式必須能夠有效率地處理三種文字：

• 符合規則運算式模式的文字。

• 不符合規則運算式模式的文字。

• 幾乎符合規則運算式模式的文字。

最後一種文字對於專為處理受限制輸入的規則運算式而言尤其繁瑣。 如果該規則運算式也依賴大量[回溯](backtracking.md)，則規則運算式引擎可能耗費相當長的時間 (有些情況需要許多小時或許多天) 處理看似無關緊要的文字。 

> [!WARNING]
> 下列範例將使用容易造成大量回溯，而且可能拒絕有效電子郵件地址的規則運算式。 這個規則運算式不應該在電子郵件驗證常式中使用。 若希望規則運算式驗證電子郵件地址，請參閱[如何：確認字串為有效的電子郵件格式](verify-format.md)。 


例如，像是驗證電子郵件地址別名的規則運算式，這種規則運算式相當常用卻也極為繁瑣。 規則運算式 `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` 主要用來處理一般視為有效的電子郵件地址，其中包含英數字元，後面接著零個或多個字元，而這些字元可以是英數字、句號或連字號。 規則運算式的結尾必須是英數字元。 不過，如下面的範例所示，雖然這個規則運算式可輕鬆處理有效的輸入，但是當它處理幾乎有效的輸入時就非常沒有效率。

```csharp
using System;
using System.Diagnostics;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      Stopwatch sw;    
      string[] addresses = { "AAAAAAAAAAA@contoso.com", 
                             "AAAAAAAAAAaaaaaaaaaa!@contoso.com" };
      // The following regular expression should not actually be used to 
      // validate an email address.
      string pattern = @"^[0-9A-Z]([-.\w]*[0-9A-Z])*$";
      string input; 

      foreach (var address in addresses) {
         string mailBox = address.Substring(0, address.IndexOf("@"));       
         int index = 0;
         for (int ctr = mailBox.Length - 1; ctr >= 0; ctr--) {
            index++;

            input = mailBox.Substring(ctr, index); 
            sw = Stopwatch.StartNew();
            Match m = Regex.Match(input, pattern, RegexOptions.IgnoreCase);
            sw.Stop();
            if (m.Success)
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed);
            else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed);
         }
         Console.WriteLine();
      }
   }
}

// The example displays output similar to the following:
//     1. Matched '                        A' in 00:00:00.0007122
//     2. Matched '                       AA' in 00:00:00.0000282
//     3. Matched '                      AAA' in 00:00:00.0000042
//     4. Matched '                     AAAA' in 00:00:00.0000038
//     5. Matched '                    AAAAA' in 00:00:00.0000042
//     6. Matched '                   AAAAAA' in 00:00:00.0000042
//     7. Matched '                  AAAAAAA' in 00:00:00.0000042
//     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
//     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
//    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
//    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
//    
//     1. Failed  '                        !' in 00:00:00.0000447
//     2. Failed  '                       a!' in 00:00:00.0000071
//     3. Failed  '                      aa!' in 00:00:00.0000071
//     4. Failed  '                     aaa!' in 00:00:00.0000061
//     5. Failed  '                    aaaa!' in 00:00:00.0000081
//     6. Failed  '                   aaaaa!' in 00:00:00.0000126
//     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
//     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
//     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
//    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
//    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
//    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
//    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
//    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
//    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
//    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
//    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
//    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
//    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
//    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
//    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

```vb
Imports System.Diagnostics
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim sw As Stopwatch    
      Dim addresses() As String = { "AAAAAAAAAAA@contoso.com", 
                                 "AAAAAAAAAAaaaaaaaaaa!@contoso.com" }
      ' The following regular expression should not actually be used to 
      ' validate an email address.
      Dim pattern As String = "^[0-9A-Z]([-.\w]*[0-9A-Z])*$"
      Dim input As String 

      For Each address In addresses
         Dim mailBox As String = address.Substring(0, address.IndexOf("@"))       
         Dim index As Integer = 0
         For ctr As Integer = mailBox.Length - 1 To 0 Step -1
            index += 1
            input = mailBox.Substring(ctr, index) 
            sw = Stopwatch.StartNew()
            Dim m As Match = Regex.Match(input, pattern, RegexOptions.IgnoreCase)
            sw.Stop()
            if m.Success Then
               Console.WriteLine("{0,2}. Matched '{1,25}' in {2}", 
                                 index, m.Value, sw.Elapsed)
            Else                     
               Console.WriteLine("{0,2}. Failed  '{1,25}' in {2}", 
                                 index, input, sw.Elapsed)
            End If                  
         Next
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays output similar to the following:
'     1. Matched '                        A' in 00:00:00.0007122
'     2. Matched '                       AA' in 00:00:00.0000282
'     3. Matched '                      AAA' in 00:00:00.0000042
'     4. Matched '                     AAAA' in 00:00:00.0000038
'     5. Matched '                    AAAAA' in 00:00:00.0000042
'     6. Matched '                   AAAAAA' in 00:00:00.0000042
'     7. Matched '                  AAAAAAA' in 00:00:00.0000042
'     8. Matched '                 AAAAAAAA' in 00:00:00.0000087
'     9. Matched '                AAAAAAAAA' in 00:00:00.0000045
'    10. Matched '               AAAAAAAAAA' in 00:00:00.0000045
'    11. Matched '              AAAAAAAAAAA' in 00:00:00.0000045
'    
'     1. Failed  '                        !' in 00:00:00.0000447
'     2. Failed  '                       a!' in 00:00:00.0000071
'     3. Failed  '                      aa!' in 00:00:00.0000071
'     4. Failed  '                     aaa!' in 00:00:00.0000061
'     5. Failed  '                    aaaa!' in 00:00:00.0000081
'     6. Failed  '                   aaaaa!' in 00:00:00.0000126
'     7. Failed  '                  aaaaaa!' in 00:00:00.0000359
'     8. Failed  '                 aaaaaaa!' in 00:00:00.0000414
'     9. Failed  '                aaaaaaaa!' in 00:00:00.0000758
'    10. Failed  '               aaaaaaaaa!' in 00:00:00.0001462
'    11. Failed  '              aaaaaaaaaa!' in 00:00:00.0002885
'    12. Failed  '             Aaaaaaaaaaa!' in 00:00:00.0005780
'    13. Failed  '            AAaaaaaaaaaa!' in 00:00:00.0011628
'    14. Failed  '           AAAaaaaaaaaaa!' in 00:00:00.0022851
'    15. Failed  '          AAAAaaaaaaaaaa!' in 00:00:00.0045864
'    16. Failed  '         AAAAAaaaaaaaaaa!' in 00:00:00.0093168
'    17. Failed  '        AAAAAAaaaaaaaaaa!' in 00:00:00.0185993
'    18. Failed  '       AAAAAAAaaaaaaaaaa!' in 00:00:00.0366723
'    19. Failed  '      AAAAAAAAaaaaaaaaaa!' in 00:00:00.1370108
'    20. Failed  '     AAAAAAAAAaaaaaaaaaa!' in 00:00:00.1553966
'    21. Failed  '    AAAAAAAAAAaaaaaaaaaa!' in 00:00:00.3223372
```

如範例的輸出所示，規則運算式引擎會以大致相同的時間間隔處理有效的電子郵件別名 (無論其長度為何)。 但另一方面，當幾乎有效的電子郵件地址包含超過五個字元時，字串中超出的每個字元其處理時間約為兩倍。 這表示，幾乎有效的 28 個字元字串需要超過一小時的處理時間，而幾乎有效的 33 個字元字串則需要將近一天來處理。 

由於這個規則運算式單純是考量所要比對輸入的格式而開發，因此並未考慮不符合模式的輸入。 而這種情況就會讓幾乎符合規則運算式模式的未受限制輸入大幅降低效能。

若要解決這個問題，您可以執行下列操作：

* 開發模式時，您應考慮回溯可能對規則運算式引擎的效能造成的影響，尤其是規則運算式的設計為處理未受限制的輸入。 如需詳細資訊，請參閱[控制回溯](#take-charge-of-backtracking)一節。

* 使用無效或幾乎有效的輸入以及有效輸入徹底測試您的規則運算式。 若要針對特殊規則運算式隨機產生輸入，您可以使用 [Rex](http://research.microsoft.com/en-us/projects/rex/)，這是 Microsoft Research 提供的規則運算式探索工具。

## <a name="handle-object-instantiation-appropriately"></a>適當處理物件具現化

[System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) 類別是 .NET 規則運算式物件模型的核心，它代表規則運算式引擎。 使用 [Regex](xref:System.Text.RegularExpressions.Regex) 引擎的方式經常是影響規則運算式效能最重要的一項因素。 定義規則運算式的工作與結合規則運算式引擎和規則運算式模式息息相關。 無論是傳遞規則運算式模式給 [Regex](xref:System.Text.RegularExpressions.Regex) 物件的建構函式，藉此將該物件具現化，或是將規則運算式模式連同要分析的字串一併傳遞給靜態方法，藉此呼叫該方法，這個結合的過程都必然相當昂貴。

您可以結合規則運算式引擎與特定規則運算式模式，然後使用引擎透過數種方式比對文字：

* 您可以呼叫靜態模式比對方法，例如 [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String))。 這樣就不需要具現化規則運算式物件。

* 您可以具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件，並且呼叫解譯之規則運算式的執行個體模式比對方法。 這是將規則運算式引擎繫結至規則運算式模式的預設方法。 這個方法會在 [Regex](xref:System.Text.RegularExpressions.Regex) 物件具現化，但是沒有包含 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 旗標的 options 引數時得出結果。

* 您可以具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件，並且呼叫編譯之規則運算式的執行個體模式比對方法。 當 [Regex](xref:System.Text.RegularExpressions.Regex) 物件具現化且包含 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 旗標的 options 引數時，規則運算式物件就會表示編譯的模式。

> [!IMPORTANT]
> 如果在方法呼叫中重複使用相同的規則運算式，或是應用程式大量使用規則運算式物件，則方法呼叫的形式 (靜態、解譯、編譯) 就會影響效能。
 
### <a name="static-regular-expressions"></a>靜態規則運算式

建議您使用靜態規則運算式方法來替代使用相同的規則運算式重複具現化規則運算式物件。 與規則運算式物件所使用的規則運算式模式不同的是，規則運算式引擎會在內部快取作業程式碼或是從執行個體方法呼叫中所使用模式編譯的 Microsoft intermediate language (MSIL)。 

例如，您可以呼叫方法來驗證使用者輸入。 在此範例中，一個名為 `IsValidCurrency` 的方法會檢查使用者是否已輸入貨幣符號且後面至少有一個十進位數字。 下列範例示範非常沒有效率的 `IsValidCurrency` 方法實作。 請注意，每一個方法呼叫都會使用相同的模式重複具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件。 而這表示，每次呼叫方法時都必須重新編譯規則運算式。

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      Regex currencyRegex = new Regex(pattern);
      return currencyRegex.IsMatch(currencyValue);
   }
}
```

```vb
Public Sub OKButton_Click(sender As Object, e As EventArgs) _ 
           Handles OKButton.Click

   If Not String.IsNullOrEmpty(sourceCurrency.Text) Then
      If RegexLib.IsValidCurrency(sourceCurrency.Text) Then
         PerformConversion()
      Else
         status.Text = "The source currency value is invalid."
      End If          
   End If
End Sub
```

您應該用呼叫靜態 [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) 方法取代這個沒有效率的程式碼。 這樣就不必在每次您想要呼叫模式比對方法時具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件，並且可讓規則運算式引擎從其快取擷取編譯版的規則運算式。

```csharp
using System;
using System.Text.RegularExpressions;

public class RegexLib
{
   public static bool IsValidCurrency(string currencyValue)
   {
      string pattern = @"\p{Sc}+\s*\d+";
      return Regex.IsMatch(currencyValue, pattern); 
   }
}
```

```vb
Imports System.Text.RegularExpressions

Public Module RegexLib
   Public Function IsValidCurrency(currencyValue As String) As Boolean
      Dim pattern As String = "\p{Sc}+\s*\d+"
      Return Regex.IsMatch(currencyValue, pattern)
   End Function
End Module
```

根據預設，會快取 15 個最近使用的靜態規則運算式模式。 針對需要大量快取之靜態規則運算式的應用程式，快取的大小可以透過設定 [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) 屬性加以調整。

這個範例中使用的規則運算式 `\p{Sc}+\s*\d+` 會驗證輸入字串是否包含貨幣符號和至少一個十進位數字。 模式的定義方式如下表所示。

模式 | 描述
------- | -----------
`\p{Sc}+` | 比對 [Unicode Symbol, Currency] 分類中的一個或多個字元。
`\s*` | 比對零個以上的空白字元。
`\d+` | 比對一個或多個十進位數字。
 
### <a name="interpreted-vs-compiled-regular-expressions"></a>比較經過解譯與經過編譯的規則運算式

未透過指定 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項繫結至規則運算式引擎的規則運算式模式會加以解譯。 具現化規則運算式物件時，規則運算式引擎會將規則運算式轉換成一組作業程式碼。 呼叫執行個體方法時，作業程式碼會轉換成 MSIL 並且由 JIT 編譯器執行。 同樣地，當呼叫靜態規則運算式方法而快取中找不到規則運算式時，規則運算式引擎會將規則運算式轉換成一組作業程式碼，並且將它們儲存到快取中。 然後引擎會將這些作業程式碼轉換成 MSIL，JIT 編譯器就可以執行這些作業程式碼。 解譯的規則運算式會藉由放慢執行時間來縮短啟動時間。 因此，在少數方法呼叫中使用規則運算式時，或是雖然不知道規則運算式方法呼叫的確實數目，但是期望數目很少時，最適合使用解譯的規則運算式。 隨著方法呼叫的數目增加，放慢執行速度就會壓縮掉縮短啟動時間所獲得的效能。

透過指定 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項繫結至規則運算式引擎的規則運算式模式會加以編譯。 這表示，當具現化規則運算式物件，或是當呼叫靜態規則運算式方法而快取中找不到規則運算式時，規則運算式引擎會將規則運算式轉換成一組中繼的作業程式碼，然後將這些程式碼轉換成 MSIL。 呼叫方法時，JIT 編譯器會執行 MSIL。 與解譯的規則運算式相反的是，編譯的規則運算式會延長啟動時間，但加快執行個別模式比對方法的速度。 因此，編譯規則運算式所獲得的效能優勢會與呼叫的規則運算式方法數目成比例。

簡言之，我們建議您在呼叫含有相對較不常用之特定規則運算式的規則運算式方法時，使用解譯的規則運算式。 而當您呼叫含有相對較常用之特定規則運算式的規則運算式方法時，則應該使用編譯的規則運算式。 無論是放慢解譯的規則運算式執行速度所提升的效能超過縮短的啟動時間，或是放慢編譯的規則運算式啟動時間所提升的效能超過加快執行速度，都不容易判斷出其確實的臨界值。 因為臨界值取決於各種不同的因素，包括規則運算式及其處理之特定資料的複雜度。 若要判斷究竟是解譯或編譯的規則運算式能為您的特殊應用程式案例提供最佳效能，您可以使用 [Stopwatch](xref:System.Diagnostics.Stopwatch) 類別比較兩者的執行時間。

下列範例會比較編譯和解譯的規則運算式讀取 Theodore Dreiser 所著 "The Financier" 一文的前十個句子及讀取所有句子時的效能。 如範例的輸出所示，僅對規則運算式比對方法進行十次呼叫時，解譯的規則運算式能提供比編譯的規則運算式更佳的效能。 但是進行大量呼叫 (此案例中為超過 13,000 次) 時，編譯的規則運算式會提供較佳的效能。 

```csharp
using System;
using System.Diagnostics;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]";
      Stopwatch sw;
      Match match;
      int ctr;

      StreamReader inFile = new StreamReader(@".\Dreiser_TheFinancier.txt");
      string input = inFile.ReadToEnd();
      inFile.Close();

      // Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex int10 = new Regex(pattern, RegexOptions.Singleline);
      match = int10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex comp10 = new Regex(pattern, 
                   RegexOptions.Singleline | RegexOptions.Compiled);
      match = comp10.Match(input);
      for (ctr = 0; ctr <= 9; ctr++) {
         if (match.Success)
            // Do nothing with the match except get the next match.
            match = match.NextMatch();
         else
            break;
      }
      sw.Stop();
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed);

      // Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:");
      sw = Stopwatch.StartNew();
      Regex intAll = new Regex(pattern, RegexOptions.Singleline);
      match = intAll.Match(input);
      int matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);

      // Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:");
      sw = Stopwatch.StartNew();
      Regex compAll = new Regex(pattern, 
                      RegexOptions.Singleline | RegexOptions.Compiled);
      match = compAll.Match(input);
      matches = 0;
      while (match.Success) {
         matches++;
         // Do nothing with the match except get the next match.
         match = match.NextMatch();
      }
      sw.Stop();
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed);      
   }
}
// The example displays the following output:
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0047491
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0141872
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1929928
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7635869
//       
//       >compare1
//       10 Sentences with Interpreted Regex:
//          10 matches in 00:00:00.0046914
//       10 Sentences with Compiled Regex:
//          10 matches in 00:00:00.0143727
//       All Sentences with Interpreted Regex:
//          13,443 matches in 00:00:01.1514100
//       All Sentences with Compiled Regex:
//          13,443 matches in 00:00:00.7432921
```

```vb
Imports System.Diagnostics
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]"
      Dim sw As Stopwatch
      Dim match As Match
      Dim ctr As Integer

      Dim inFile As New StreamReader(".\Dreiser_TheFinancier.txt")
      Dim input As String = inFile.ReadToEnd()
      inFile.Close()

      ' Read first ten sentences with interpreted regex.
      Console.WriteLine("10 Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim int10 As New Regex(pattern, RegexOptions.SingleLine)
      match = int10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read first ten sentences with compiled regex.
      Console.WriteLine("10 Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim comp10 As New Regex(pattern, 
                   RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = comp10.Match(input)
      For ctr = 0 To 9
         If match.Success Then
            ' Do nothing with the match except get the next match.
            match = match.NextMatch()
         Else
            Exit For
         End If
      Next
      sw.Stop()
      Console.WriteLine("   {0} matches in {1}", ctr, sw.Elapsed)

      ' Read all sentences with interpreted regex.
      Console.WriteLine("All Sentences with Interpreted Regex:")
      sw = Stopwatch.StartNew()
      Dim intAll As New Regex(pattern, RegexOptions.SingleLine)
      match = intAll.Match(input)
      Dim matches As Integer = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)

      ' Read all sentnces with compiled regex.
      Console.WriteLine("All Sentences with Compiled Regex:")
      sw = Stopwatch.StartNew()
      Dim compAll As New Regex(pattern, 
                     RegexOptions.SingleLine Or RegexOptions.Compiled)
      match = compAll.Match(input)
      matches = 0
      Do While match.Success
         matches += 1
         ' Do nothing with the match except get the next match.
         match = match.NextMatch()
      Loop
      sw.Stop()
      Console.WriteLine("   {0:N0} matches in {1}", matches, sw.Elapsed)      
   End Sub
End Module
' The example displays output like the following:
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0047491
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0141872
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1929928
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7635869
'       
'       >compare1
'       10 Sentences with Interpreted Regex:
'          10 matches in 00:00:00.0046914
'       10 Sentences with Compiled Regex:
'          10 matches in 00:00:00.0143727
'       All Sentences with Interpreted Regex:
'          13,443 matches in 00:00:01.1514100
'       All Sentences with Compiled Regex:
'          13,443 matches in 00:00:00.7432921
```

範例中所使用規則運算式模式 `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]` 的定義方式如下表所示。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`\w+` | 比對一個或多個文字字元。
`(\r?\n)|,?\s)` | 比對後面接著新行字元的零個或一個歸位字元，或是後面接著空白字元的零個或一個逗號。
`(\w+((\r?\n)|,?\s))*` | 比對出現零次或多次的一個或多個文字字元，其後面會接著零個或一個歸位字元和新行字元，或是後面接著空白字元的零個或一個逗號。
`\w+` | 比對一個或多個文字字元。
`[.?:;!]` | 比對句號、問號、冒號、分號或驚嘆號。
 
## <a name="take-charge-of-backtracking"></a>控制回溯

通常規則運算式引擎會使用線性迴歸逐一處理輸入字串，並且與規則運算式模式比較。 不過，當規則運算式模式中使用不定數的數量詞 (例如 __*__、**+** 和 **?**) 時，規則運算式引擎可能會放棄一部分成功的部分符合結果，並且返回之前儲存的狀態，以便搜尋與整個模式完全相符的結果。 這個程序稱為「回溯」(Backtracking)。

> [!NOTE]
> 如需回溯的詳細資訊，請參閱[規則運算式行為的詳細資料](regex-behavior.md)及[規則運算式中的回溯](backtracking.md)。
 
支援回溯能讓規則運算式更強大且更靈活， 同時還能讓規則運算式開發人員負責掌控規則運算式引擎的作業。 由於開發人員經常忽略這個責任而誤用回溯或大量使用回溯，因而時常是造成規則運算式效能低落的最重要原因。 在最糟的情況下，輸入字串中每個超出字元的執行時間可能會倍增。 事實上，如果輸入幾乎符合規則運算式模式的話，大量使用回溯很容易製造相當於程式設計上的無窮迴圈，而規則運算式引擎可能需要數小時，甚至數天來處理相對來說很短的輸入字串。

儘管回溯並不是比對的要件，應用程式常常會因為使用回溯而影響效能。 例如，規則運算式 `\b\p{Lu}\w*\b` 會比對所有開頭為大寫字元的文字，如下表所示。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`\p{Lu}` | 比對大寫字元。
`\w*` | 比對零個或多個文字字元。
`\b` | 結束字緣比對。
 
由於字緣與文字字元不同，也不是文字字元的子集，因此規則運算式引擎不可能在比對文字字元時跨越字緣。 這表示對於這個規則運算式來說，回溯不會使任何比對完全成功，只會造成效能降低，因為規則運算式引擎會被迫儲存每一個成功的初始文字字元比對的狀態。

如果您判定不需要回溯，可以使用 **(?>**_subexpression_**)** 語言項目將它停用。 下列範例會使用兩個規則運算式剖析輸入字串。 首先，`\b\p{Lu}\w*\b` 會仰賴回溯。 第二，`\b\p{Lu}(?>\w*)\b` 會停用回溯。 如範例的輸出所示，兩者會產生相同的結果。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This this word Sentence name Capital";
      string pattern = @"\b\p{Lu}\w*\b";
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);

      Console.WriteLine();

      pattern = @"\b\p{Lu}(?>\w*)\b";   
      foreach (Match match in Regex.Matches(input, pattern))
         Console.WriteLine(match.Value);
   }
}
// The example displays the following output:
//       This
//       Sentence
//       Capital
//       
//       This
//       Sentence
//       Capital
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This this word Sentence name Capital"
      Dim pattern As String = "\b\p{Lu}\w*\b"
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
      Console.WriteLine()

      pattern = "\b\p{Lu}(?>\w*)\b"   
      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine(match.Value)
      Next
   End Sub
End Module
' The example displays the following output:
'       This
'       Sentence
'       Capital
'       
'       This
'       Sentence
'       Capital
```

在許多情況下，回溯是比對規則運算式模式與輸入文字時所必要。 不過，大量回溯可能嚴重降低效能，並且製造應用程式停止回應的印象。 尤其是當數量詞為巢狀，而且符合外部子運算式的文字是符合內部子運算式之文字的子集時，就會發生這種情況。 

> [!WARNING]
> 除了避免大量回溯以外，您應該使用逾時功能確保大量回溯不會嚴重降低規則運算式的效能。 如需詳細資訊，請參閱[使用逾時值](#use-time-out-values)一節。
 
例如，規則運算式模式 `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` 的目的在於比對至少包含一個英數字元的零件編號。 任何額外的字元都可能包含英數字元、連字號、底線或句號，不過最後一個字元必須是英數字。 $ 符號則結束零件編號。 在某些情況下，這個規則運算式模式可能顯現出極差的效能，因為數量詞為巢狀，而且子運算式 `[0-9A-Z]` 是 `[-.\w]*` 子運算式的子集。

在這類情況下，您可以移除巢狀數量詞，並且將外部子運算式取代為零寬度的右合樣或左合樣判斷提示，藉此最佳化規則運算式的效能。 右合樣和左合樣判斷提示是錨點，它們不會移動輸入字串中的指標，而是向右或向左合樣，以檢查是否符合指定的條件。 例如，零件編號規則運算式可以重寫為 `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`。 這個規則運算式模式的定義方式如下表所示。

模式 | 描述
------- | -----------
`^` | 在輸入字串的開頭開始比對。
`[0-9A-Z]` | 比對英數字元。 零件編號必須至少包含這個字元。
`[-.\w]*` | 比對出現零次或多次的任何文字字元、連字號或句號。
`\$] | 比對 $ 符號。
`(?<=[0-9A-Z])` | 向右合樣結尾的 $ 符號，確定前一個字元是英數字。
`$` 在輸入字串結尾時結束比對。
 
下列範例說明如何使用這個規則運算式比對包含可能零件編號的陣列。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string pattern = @"^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$";
      string[] partNos = { "A1C$", "A4", "A4$", "A1603D$", "A1603D#" };

      foreach (var input in partNos) {
         Match match = Regex.Match(input, pattern);
         if (match.Success)
            Console.WriteLine(match.Value);
         else
            Console.WriteLine("Match not found.");
      }      
   }
}
// The example displays the following output:
//       A1C$
//       Match not found.
//       A4$
//       A1603D$
//       Match not found.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim pattern As String = "^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$"
      Dim partNos() As String = { "A1C$", "A4", "A4$", "A1603D$", 
                                  "A1603D#" }

      For Each input As String In partNos
         Dim match As Match = Regex.Match(input, pattern)
         If match.Success Then
            Console.WriteLine(match.Value)
         Else
            Console.WriteLine("Match not found.")
         End If
      Next      
   End Sub
End Module
' The example displays the following output:
'       A1C$
'       Match not found.
'       A4$
'       A1603D$
'       Match not found.
```

.NET 中的規則運算式語言包括下列語言項目，可讓您用來消除巢狀數量詞。 如需詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。

語言項目 | 描述
---------------- | ----------- 
**(?**=_subexpression_**)** | 零寬度右合樣。 從目前的位置向右合樣，判斷 *subexpression* 是否符合輸入字串。
**(?!**_subexpression_**)** | 零寬度右不合樣。 從目前的位置向右合樣，判斷 *subexpression* 是否不符合輸入字串。
**(?<**=_subexpression_**)** | 零寬度左合樣。 從目前的位置向左合樣，判斷 *subexpression* 是否符合輸入字串。
**(?<!**_subexpression_**)** | 零寬度左不合樣。 從目前的位置向左合樣，判斷 *subexpression* 是否不符合輸入字串。
 
## <a name="use-time-out-values"></a>使用逾時值

如果您的規則運算式會處理幾乎符合規則運算式模式的輸入，它經常會依賴大量回溯，如此就會大幅影響其效能。 除了仔細考量使用回溯以及對幾乎符合的輸入進行規則運算式測試之外，務必要設定逾時值，以確保將大量回溯 (如發生的話) 的影響降至最低。

規則運算式逾時間隔會定義規則運算式引擎在逾時前，將尋找單一相符項目的一段時間。 預設的逾時間隔是 [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout)，這表示規則運算式不會逾時。 您可以依照下述方式覆寫這個值並定義逾時間隔： 

* 在您呼叫 [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) 建構函式具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件時提供逾時值。

* 呼叫靜態模式比對方法，例如，包含 *matchTimeout* 參數的 [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) 或 [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan))。

如果您已定義逾時間隔，但是在該間隔結束時未找到相符項目，則規則運算式方法會擲回 [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) 例外狀況。 在例外處理常式中，您可以選擇以較長的逾時間隔重試比對、放棄比對嘗試並假設沒有相符項目，或是放棄比對嘗試並記錄例外狀況資訊供未來進行分析。

下列範例將定義 `GetWordData` 方法，該方法會具現化逾時間隔為 350 毫秒的規則運算式，以計算文字文件中的字數和一個字的平均字元數。 如果比對作業逾時，則逾時間隔將增加 350 毫秒，並且重新具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件。 如果新的逾時間隔超過 1 秒，則方法會重新擲回例外狀況至呼叫端。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      RegexUtilities util = new RegexUtilities();
      string title = "Doyle - The Hound of the Baskervilles.txt";
      try {
         var info = util.GetWordData(title);
         Console.WriteLine("Words:               {0:N0}", info.Item1);
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2); 
      }
      catch (IOException e) {
         Console.WriteLine("IOException reading file '{0}'", title);
         Console.WriteLine(e.Message);
      }
      catch (RegexMatchTimeoutException e) {
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds);
      }
   }
}

public class RegexUtilities
{
   public Tuple<int, double> GetWordData(string filename)
   { 
      const int MAX_TIMEOUT = 1000;   // Maximum timeout interval in milliseconds.
      const int INCREMENT = 350;      // Milliseconds increment of timeout.

      List<string> exclusions = new List<string>( new string[] { "a", "an", "the" });
      int[] wordLengths = new int[29];        // Allocate an array of more than ample size.
      string input = null;
      StreamReader sr = null;
      try { 
         sr = new StreamReader(filename);
         input = sr.ReadToEnd();
      }
      catch (FileNotFoundException e) {
         string msg = String.Format("Unable to find the file '{0}'", filename);
         throw new IOException(msg, e);
      }
      catch (IOException e) {
         throw new IOException(e.Message, e);
      }
      finally {
         if (sr != null) sr.Close(); 
      }

      int timeoutInterval = INCREMENT;
      bool init = false;
      Regex rgx = null;
      Match m = null;
      int indexPos = 0;  
      do {
         try {
            if (! init) {
               rgx = new Regex(@"\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval));
               m = rgx.Match(input, indexPos);
               init = true;
            }
            else { 
               m = m.NextMatch();
            }
            if (m.Success) {    
               if ( !exclusions.Contains(m.Value.ToLower()))
                  wordLengths[m.Value.Length]++;

               indexPos += m.Length + 1;   
            }
         }
         catch (RegexMatchTimeoutException e) {
            if (e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT) {
               timeoutInterval += INCREMENT;
               init = false;
            }
            else {
               // Rethrow the exception.
               throw; 
            }   
         }          
      } while (m.Success);

      // If regex completed successfully, calculate number of words and average length.
      int nWords = 0; 
      long totalLength = 0;

      for (int ctr = wordLengths.GetLowerBound(0); ctr <= wordLengths.GetUpperBound(0); ctr++) {
         nWords += wordLengths[ctr];
         totalLength += ctr * wordLengths[ctr];
      }
      return new Tuple<int, double>(nWords, totalLength/nWords);
   }
}
```

```vb
Imports System.Collections.Generic
Imports System.IO
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim util As New RegexUtilities()
      Dim title As String = "Doyle - The Hound of the Baskervilles.txt"
      Try
         Dim info = util.GetWordData(title)
         Console.WriteLine("Words:               {0:N0}", info.Item1)
         Console.WriteLine("Average Word Length: {0:N2} characters", info.Item2) 
      Catch e As IOException
         Console.WriteLine("IOException reading file '{0}'", title)
         Console.WriteLine(e.Message)
      Catch e As RegexMatchTimeoutException
         Console.WriteLine("The operation timed out after {0:N0} milliseconds", 
                           e.MatchTimeout.TotalMilliseconds)
      End Try
   End Sub
End Module

Public Class RegexUtilities
   Public Function GetWordData(filename As String) As Tuple(Of Integer, Double) 
      Const MAX_TIMEOUT As Integer = 1000  ' Maximum timeout interval in milliseconds.
      Const INCREMENT As Integer = 350     ' Milliseconds increment of timeout.

      Dim exclusions As New List(Of String)({"a", "an", "the" })
      Dim wordLengths(30) As Integer        ' Allocate an array of more than ample size.
      Dim input As String = Nothing
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader(filename)
         input = sr.ReadToEnd()
      Catch e As FileNotFoundException
         Dim msg As String = String.Format("Unable to find the file '{0}'", filename)
         Throw New IOException(msg, e)
      Catch e As IOException
         Throw New IOException(e.Message, e)
      Finally
         If sr IsNot Nothing Then sr.Close() 
      End Try

      Dim timeoutInterval As Integer = INCREMENT
      Dim init As Boolean = False
      Dim rgx As Regex = Nothing
      Dim m As Match = Nothing
      Dim indexPos As Integer = 0  
      Do
         Try
            If Not init Then
               rgx = New Regex("\b\w+\b", RegexOptions.None, 
                               TimeSpan.FromMilliseconds(timeoutInterval))
               m = rgx.Match(input, indexPos)
               init = True
            Else 
               m = m.NextMatch()
            End If
            If m.Success Then    
               If Not exclusions.Contains(m.Value.ToLower()) Then
                  wordLengths(m.Value.Length) += 1
               End If
               indexPos += m.Length + 1   
            End If
         Catch e As RegexMatchTimeoutException
            If e.MatchTimeout.TotalMilliseconds < MAX_TIMEOUT Then
               timeoutInterval += INCREMENT
               init = False
            Else
               ' Rethrow the exception.
               Throw 
            End If   
         End Try          
      Loop While m.Success

      ' If regex completed successfully, calculate number of words and average length.
      Dim nWords As Integer
      Dim totalLength As Long

      For ctr As Integer = wordLengths.GetLowerBound(0) To wordLengths.GetUpperBound(0)
         nWords += wordLengths(ctr)
         totalLength += ctr * wordLengths(ctr)
      Next
      Return New Tuple(Of Integer, Double)(nWords, totalLength/nWords)
   End Function
End Class
```

## <a name="capture-only-when-necessary"></a>必要時擷取

.NET 中的規則運算式支援許多群組建構，可讓您將規則運算式模式與一或多個子運算式設為群組。 .NET 規則運算式語言中最常用的群組建構為 **(**_subexpression_**)** (用於定義編號擷取群組) 和 **(?<*_name_**>**_subexpression_**)** (用於定義具名擷取群組)。 群組建構是建立反向參考和定義套用數量詞之子運算式的要件。 

不過，使用這些語言項目也有其代價。 這些語言項目會造成在 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性傳回的 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件中填入最近使用的未命名或具名擷取，而如果單一群組建構擷取了輸入字串中的多個子字串，則這些語言項目也會在特定擷取群組的 [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) 屬性傳回的 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件中填入多個 [Capture](xref:System.Text.RegularExpressions.Capture) 物件。

通常在規則運算式中使用群組建構的目的在於能夠套用數量詞，而且後續不會使用這些子運算式擷取的群組。 例如，規則運算式 `\b(\w+[;,]?\s?)+[.?!]` 是設計用來擷取整個句子。 下表描述這個規則運算式模式中的語言項目，及其對於 [Match](xref:System.Text.RegularExpressions.Match) 物件的 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 和 [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) 集合造成的影響。

模式 | 描述
------- | -----------
`\b` | 開始字緣比對。
`\w+` | 比對一個或多個文字字元。
`[;,]?` | 比對零個或一個逗號或分號。
`\s?` | 比對零個或一個空白字元。
`(\w+[;,]?\s?)+` | 比對出現一次或多次的一個或多個文字字元，後面接著選擇性的逗號或分號，再後面接著選擇性的空白字元。 這會定義必要的第一個擷取群組，如此多個文字字元 (也就是文字) 後面接著選擇性標點符號的組合才會重複，直到規則運算式引擎到達句尾為止。
`[.?!]` | 比對句號、問號或驚嘆號。
 
如下列範例所示，找到符合的結果時，[GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 和 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件中都會填入比對所擷取的項目。 在此案例中，擷取群組 `(\w+[;,]?\s?)` 會存在，如此 **+** 數量詞就能套用至其中，這樣就能讓規則運算式模式比對句子中的每個字。 否則就會比對句子中的最後一個字。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//          Group 1: 'sentence' at index 12.
//             Capture 0: 'This ' at 0.
//             Capture 1: 'is ' at 5.
//             Capture 2: 'one ' at 8.
//             Capture 3: 'sentence' at 12.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
//          Group 1: 'another' at index 30.
//             Capture 0: 'This ' at 22.
//             Capture 1: 'is ' at 27.
//             Capture 2: 'another' at 30.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'          Group 1: 'sentence' at index 12.
'             Capture 0: 'This ' at 0.
'             Capture 1: 'is ' at 5.
'             Capture 2: 'one ' at 8.
'             Capture 3: 'sentence' at 12.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
'          Group 1: 'another' at index 30.
'             Capture 0: 'This ' at 22.
'             Capture 1: 'is ' at 27.
'             Capture 2: 'another' at 30.
```

如果您使用子運算式的目的只是要在其中套用數量詞，對於擷取的文字並不感興趣，則應該停用群組擷取。 例如，**(?:**_subexpression_**)** 語言項目會阻止套用該語言項目的群組擷取相符的子字串。 在下列範例中，前一個範例的規則運算式模式會變成 `\b(?:\w+[;,]?\s?)+[.?!]`。 如輸出所示，它會阻止規則運算式引擎填入 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 和 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 集合。

```csharp
using System;
using System.Text.RegularExpressions;

public class Example
{
   public static void Main()
   {
      string input = "This is one sentence. This is another.";
      string pattern = @"\b(?:\w+[;,]?\s?)+[.?!]";

      foreach (Match match in Regex.Matches(input, pattern)) {
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index);
         int grpCtr = 0;
         foreach (Group grp in match.Groups) {
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index);
            int capCtr = 0;
            foreach (Capture cap in grp.Captures) {
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index);
               capCtr++;
            }
            grpCtr++;
         }          
         Console.WriteLine();        
      }
   }
}
// The example displays the following output:
//       Match: 'This is one sentence.' at index 0.
//          Group 0: 'This is one sentence.' at index 0.
//             Capture 0: 'This is one sentence.' at 0.
//       
//       Match: 'This is another.' at index 22.
//          Group 0: 'This is another.' at index 22.
//             Capture 0: 'This is another.' at 22.
```

```vb
Imports System.Text.RegularExpressions

Module Example
   Public Sub Main()
      Dim input As String = "This is one sentence. This is another."
      Dim pattern As String = "\b(?:\w+[;,]?\s?)+[.?!]"

      For Each match As Match In Regex.Matches(input, pattern)
         Console.WriteLine("Match: '{0}' at index {1}.", 
                           match.Value, match.Index)
         Dim grpCtr As Integer = 0
         For Each grp As Group In match.Groups
            Console.WriteLine("   Group {0}: '{1}' at index {2}.",
                              grpCtr, grp.Value, grp.Index)
            Dim capCtr As Integer = 0
            For Each cap As Capture In grp.Captures
               Console.WriteLine("      Capture {0}: '{1}' at {2}.",
                                 capCtr, cap.Value, cap.Index)
               capCtr += 1
            Next
            grpCtr += 1
         Next          
         Console.WriteLine()        
      Next    
   End Sub
End Module
' The example displays the following output:
'       Match: 'This is one sentence.' at index 0.
'          Group 0: 'This is one sentence.' at index 0.
'             Capture 0: 'This is one sentence.' at 0.
'       
'       Match: 'This is another.' at index 22.
'          Group 0: 'This is another.' at index 22.
'             Capture 0: 'This is another.' at 22.
```

您可以透過下列其中一種方式停用擷取：

* 使用 **(?:**_subexpression_**)** 語言項目。 這個項目會阻止在套用該項目的群組中擷取相符的子字串。 不過，它不會停用任何巢狀群組中的子字串擷取。

* 使用 [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) 選項。 這個選項會停用規則運算式模式中的所有未命名或隱含擷取。 當您使用這個選項時，只會擷取符合 **(?<**_name_**>**_subexpression_**)** 語言項目所定義之具名群組的子字串。 [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) 旗標可以傳遞至 [Regex](xref:System.Text.RegularExpressions.Regex)類別建構函式的 options 參數，或是 [Regex](xref:System.Text.RegularExpressions.Regex) 靜態比對方法的 options 參數。

* 在 **(?imnsx)** 語言項目中使用 **n** 選項。 這個選項會從規則運算式模式中出現該項目的位置開始，停用所有未命名或隱含擷取。 在到達模式結尾或 **(-n)** 選項啟用未命名或隱含擷取之前，擷取都會是停用狀態。 如需詳細資訊，請參閱[規則運算式中的其他建構](miscellaneous.md)。

* 在 **(?imnsx:**_subexpression_**)** 語言項目中使用 **n** 選項。 這個選項會停用 *subexpression* 中的所有未命名或隱含擷取。 任何未命名或隱含巢狀擷取群組所進行的擷取也都會停用。

## <a name="related-topics"></a>相關主題

標題 | 說明
----- | ----------- 
[規則運算式行為的詳細資料](regex-behavior.md) | 檢查 .NET 中規則運算式引擎的實作。 本主題將強調規則運算式的靈活度，並且說明開發人員應負責確保規則運算式引擎有效率且穩定地運作。
[規則運算式中的回溯](backtracking.md) | 說明何謂回溯以及回溯如何影響規則運算式的效能，並且檢查提供回溯之替代方式的語言項目。
[規則運算式語言 - 快速參考](quick-ref.md) | 描述 .NET 中規則運算式語言的項目，並且提供每個語言項目之詳細文件的連結。
 



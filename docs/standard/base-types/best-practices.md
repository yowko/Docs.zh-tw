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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: cf9c83de791fa4990a991689a26d4bbdd84cfe7d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="best-practices-for-regular-expressions"></a><span data-ttu-id="c5cae-104">規則運算式的最佳做法</span><span class="sxs-lookup"><span data-stu-id="c5cae-104">Best practices for regular expressions</span></span>

<span data-ttu-id="c5cae-105">.NET 中的規則運算式引擎是一項強大而功能完整的工具，會依據模式比對而非比較與比對常值文字的方式處理文字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-105">The regular expression engine in .NET is a powerful, full-featured tool that processes text based on pattern matches rather than on comparing and matching literal text.</span></span> <span data-ttu-id="c5cae-106">在大部分情況下，它會快速且有效率地執行模式比對。</span><span class="sxs-lookup"><span data-stu-id="c5cae-106">In most cases, it performs pattern matching rapidly and efficiently.</span></span> <span data-ttu-id="c5cae-107">不過，在某些情況下，規則運算式引擎速度可能變得相當慢。</span><span class="sxs-lookup"><span data-stu-id="c5cae-107">However, in some cases, the regular expression engine can appear to be very slow.</span></span> <span data-ttu-id="c5cae-108">而只有鮮少情況下，它甚至可能在處理相對小的輸入卻耗費數小時甚至數天時停止回應。</span><span class="sxs-lookup"><span data-stu-id="c5cae-108">In extreme cases, it can even appear to stop responding as it processes a relatively small input over the course of hours or even days.</span></span> 

<span data-ttu-id="c5cae-109">本主題說明一些開發人員可以採用的最佳做法，確保其規則運算式達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-109">This topic outlines some of the best practices that developers can adopt to ensure that their regular expressions achieve optimal performance.</span></span> <span data-ttu-id="c5cae-110">它包含以下各節：</span><span class="sxs-lookup"><span data-stu-id="c5cae-110">It contains the following sections:</span></span>

* [<span data-ttu-id="c5cae-111">考慮輸入來源</span><span class="sxs-lookup"><span data-stu-id="c5cae-111">Consider the input source</span></span>](#consider-the-input-source)

* [<span data-ttu-id="c5cae-112">適當處理物件具現化</span><span class="sxs-lookup"><span data-stu-id="c5cae-112">Handle object instantiation appropriately</span></span>](#handle-object-instantiation-appropriately)

* [<span data-ttu-id="c5cae-113">控制回溯</span><span class="sxs-lookup"><span data-stu-id="c5cae-113">Take charge of backtracking</span></span>](#take-charge-of-backtracking)

* [<span data-ttu-id="c5cae-114">使用逾時值</span><span class="sxs-lookup"><span data-stu-id="c5cae-114">Use time-out values</span></span>](#use-time-out-values)

* [<span data-ttu-id="c5cae-115">必要時擷取</span><span class="sxs-lookup"><span data-stu-id="c5cae-115">Capture only when necessary</span></span>](#capture-only-when-necessary)

* [<span data-ttu-id="c5cae-116">相關主題</span><span class="sxs-lookup"><span data-stu-id="c5cae-116">Related topics</span></span>](#related-topics)

## <a name="consider-the-input-source"></a><span data-ttu-id="c5cae-117">考慮輸入來源</span><span class="sxs-lookup"><span data-stu-id="c5cae-117">Consider the input source</span></span>

<span data-ttu-id="c5cae-118">一般而言，規則運算式可以接受兩種類型的輸入：受限制或未受限制。</span><span class="sxs-lookup"><span data-stu-id="c5cae-118">In general, regular expressions can accept two types of input: constrained or unconstrained.</span></span> <span data-ttu-id="c5cae-119">受限制的輸入是來自已知或可靠來源，並且遵循預先定義格式的文字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-119">Constrained input is text that originates from a known or reliable source and follows a predefined format.</span></span> <span data-ttu-id="c5cae-120">未受限制的輸入是來自不可靠來源 (例如 Web 使用者) 的文字，且可能未依循預先定義或預期的格式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-120">Unconstrained input is text that originates from an unreliable source, such as a web user, and may not follow a predefined or expected format.</span></span>

<span data-ttu-id="c5cae-121">通常撰寫規則運算式模式的目的在於比對有效輸入。</span><span class="sxs-lookup"><span data-stu-id="c5cae-121">Regular expression patterns are typically written to match valid input.</span></span> <span data-ttu-id="c5cae-122">也就是說，開發人員會檢查要比對的文字，然後撰寫比對該文字的規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-122">That is, developers examine the text that they want to match and then write a regular expression pattern that matches it.</span></span> <span data-ttu-id="c5cae-123">接著開發人員會利用多個有效的輸入項目進行測試，藉此判斷此模式是否需要更正或進一步詳述。</span><span class="sxs-lookup"><span data-stu-id="c5cae-123">Developers then determine whether this pattern requires correction or further elaboration by testing it with multiple valid input items.</span></span> <span data-ttu-id="c5cae-124">當模式符合所有假設的有效輸入時，即宣告準備好實際執行，並且可以納入已發行的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="c5cae-124">When the pattern matches all presumed valid inputs, it is declared to be production-ready and can be included in a released application.</span></span> <span data-ttu-id="c5cae-125">這種方式使得規則運算式模式相當適合比對限制的輸入，</span><span class="sxs-lookup"><span data-stu-id="c5cae-125">This makes a regular expression pattern suitable for matching constrained input.</span></span> <span data-ttu-id="c5cae-126">不過卻不適合比對未受限制的輸入。</span><span class="sxs-lookup"><span data-stu-id="c5cae-126">However, it does not make it suitable for matching unconstrained input.</span></span>

<span data-ttu-id="c5cae-127">若要比對未受限制的輸入，規則運算式必須能夠有效率地處理三種文字：</span><span class="sxs-lookup"><span data-stu-id="c5cae-127">To match unconstrained input, a regular expression must be able to efficiently handle three kinds of text:</span></span>

<span data-ttu-id="c5cae-128">• 符合規則運算式模式的文字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-128">• Text that matches the regular expression pattern.</span></span>

<span data-ttu-id="c5cae-129">• 不符合規則運算式模式的文字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-129">• Text that does not match the regular expression pattern.</span></span>

<span data-ttu-id="c5cae-130">• 幾乎符合規則運算式模式的文字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-130">• Text that nearly matches the regular expression pattern.</span></span>

<span data-ttu-id="c5cae-131">最後一種文字對於專為處理受限制輸入的規則運算式而言尤其繁瑣。</span><span class="sxs-lookup"><span data-stu-id="c5cae-131">The last text type is especially problematic for a regular expression that has been written to handle constrained input.</span></span> <span data-ttu-id="c5cae-132">如果該規則運算式也依賴大量[回溯](backtracking.md)，則規則運算式引擎可能耗費相當長的時間 (有些情況需要許多小時或許多天) 處理看似無關緊要的文字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-132">If that regular expression also relies on extensive [backtracking](backtracking.md), the regular expression engine can spend an inordinate amount of time (in some cases, many hours or days) processing seemingly innocuous text.</span></span> 

> [!WARNING]
> <span data-ttu-id="c5cae-133">下列範例將使用容易造成大量回溯，而且可能拒絕有效電子郵件地址的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-133">The following example uses a regular expression that is prone to excessive backtracking and that is likely to reject valid email addresses.</span></span> <span data-ttu-id="c5cae-134">這個規則運算式不應該在電子郵件驗證常式中使用。</span><span class="sxs-lookup"><span data-stu-id="c5cae-134">You should not use it in an email validation routine.</span></span> <span data-ttu-id="c5cae-135">若希望規則運算式驗證電子郵件地址，請參閱[如何：確認字串為有效的電子郵件格式](verify-format.md)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-135">If you would like a regular expression that validates email addresses, see [How to: Verify that strings are in valid email format](verify-format.md).</span></span> 


<span data-ttu-id="c5cae-136">例如，像是驗證電子郵件地址別名的規則運算式，這種規則運算式相當常用卻也極為繁瑣。</span><span class="sxs-lookup"><span data-stu-id="c5cae-136">For example, consider a very commonly used but extremely problematic regular expression for validating the alias of an email address.</span></span> <span data-ttu-id="c5cae-137">規則運算式 `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` 主要用來處理一般視為有效的電子郵件地址，其中包含英數字元，後面接著零個或多個字元，而這些字元可以是英數字、句號或連字號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-137">The regular expression `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` is written to process what is considered to be a valid email address, which consists of an alphanumeric character, followed by zero or more characters that can be alphanumeric, periods, or hyphens.</span></span> <span data-ttu-id="c5cae-138">規則運算式的結尾必須是英數字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-138">The regular expression must end with an alphanumeric character.</span></span> <span data-ttu-id="c5cae-139">不過，如下面的範例所示，雖然這個規則運算式可輕鬆處理有效的輸入，但是當它處理幾乎有效的輸入時就非常沒有效率。</span><span class="sxs-lookup"><span data-stu-id="c5cae-139">However, as the following example shows, although this regular expression handles valid input easily, its performance is very inefficient when it is processing nearly valid input.</span></span>

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

<span data-ttu-id="c5cae-140">如範例的輸出所示，規則運算式引擎會以大致相同的時間間隔處理有效的電子郵件別名 (無論其長度為何)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-140">As the output from the example shows, the regular expression engine processes the valid email alias in about the same time interval regardless of its length.</span></span> <span data-ttu-id="c5cae-141">但另一方面，當幾乎有效的電子郵件地址包含超過五個字元時，字串中超出的每個字元其處理時間約為兩倍。</span><span class="sxs-lookup"><span data-stu-id="c5cae-141">On the other hand, when the nearly valid email address has more than five characters, processing time approximately doubles for each additional character in the string.</span></span> <span data-ttu-id="c5cae-142">這表示，幾乎有效的 28 個字元字串需要超過一小時的處理時間，而幾乎有效的 33 個字元字串則需要將近一天來處理。</span><span class="sxs-lookup"><span data-stu-id="c5cae-142">This means that a nearly valid 28-character string would take over an hour to process, and a nearly valid 33-character string would take nearly a day to process.</span></span> 

<span data-ttu-id="c5cae-143">由於這個規則運算式單純是考量所要比對輸入的格式而開發，因此並未考慮不符合模式的輸入。</span><span class="sxs-lookup"><span data-stu-id="c5cae-143">Because this regular expression was developed solely by considering the format of input to be matched, it fails to take account of input that does not match the pattern.</span></span> <span data-ttu-id="c5cae-144">而這種情況就會讓幾乎符合規則運算式模式的未受限制輸入大幅降低效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-144">This, in turn, can allow unconstrained input that nearly matches the regular expression pattern to significantly degrade performance.</span></span>

<span data-ttu-id="c5cae-145">若要解決這個問題，您可以執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="c5cae-145">To solve this problem, you can do the following:</span></span>

* <span data-ttu-id="c5cae-146">開發模式時，您應考慮回溯可能對規則運算式引擎的效能造成的影響，尤其是規則運算式的設計為處理未受限制的輸入。</span><span class="sxs-lookup"><span data-stu-id="c5cae-146">When developing a pattern, you should consider how backtracking might affect the performance of the regular expression engine, particularly if your regular expression is designed to process unconstrained input.</span></span> <span data-ttu-id="c5cae-147">如需詳細資訊，請參閱[控制回溯](#take-charge-of-backtracking)一節。</span><span class="sxs-lookup"><span data-stu-id="c5cae-147">For more information, see the [Take charge of backtracking](#take-charge-of-backtracking) section.</span></span>

* <span data-ttu-id="c5cae-148">使用無效或幾乎有效的輸入以及有效輸入徹底測試您的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-148">Thoroughly test your regular expression using invalid and near-valid input as well as valid input.</span></span> <span data-ttu-id="c5cae-149">若要針對特殊規則運算式隨機產生輸入，您可以使用 [Rex](http://research.microsoft.com/en-us/projects/rex/)，這是 Microsoft Research 提供的規則運算式探索工具。</span><span class="sxs-lookup"><span data-stu-id="c5cae-149">To generate input for a particular regular expression randomly, you can use [Rex](http://research.microsoft.com/en-us/projects/rex/), which is a regular expression exploration tool from Microsoft Research.</span></span>

## <a name="handle-object-instantiation-appropriately"></a><span data-ttu-id="c5cae-150">適當處理物件具現化</span><span class="sxs-lookup"><span data-stu-id="c5cae-150">Handle object instantiation appropriately</span></span>

<span data-ttu-id="c5cae-151">[System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) 類別是 .NET 規則運算式物件模型的核心，它代表規則運算式引擎。</span><span class="sxs-lookup"><span data-stu-id="c5cae-151">At the heart of .NET’s regular expression object model is the [System.Text.RegularExpressions.Regex](xref:System.Text.RegularExpressions.Regex) class, which represents the regular expression engine.</span></span> <span data-ttu-id="c5cae-152">使用 [Regex](xref:System.Text.RegularExpressions.Regex) 引擎的方式經常是影響規則運算式效能最重要的一項因素。</span><span class="sxs-lookup"><span data-stu-id="c5cae-152">Often, the single greatest factor that affects regular expression performance is the way in which the [Regex](xref:System.Text.RegularExpressions.Regex) engine is used.</span></span> <span data-ttu-id="c5cae-153">定義規則運算式的工作與結合規則運算式引擎和規則運算式模式息息相關。</span><span class="sxs-lookup"><span data-stu-id="c5cae-153">Defining a regular expression involves tightly coupling the regular expression engine with a regular expression pattern.</span></span> <span data-ttu-id="c5cae-154">無論是傳遞規則運算式模式給 [Regex](xref:System.Text.RegularExpressions.Regex) 物件的建構函式，藉此將該物件具現化，或是將規則運算式模式連同要分析的字串一併傳遞給靜態方法，藉此呼叫該方法，這個結合的過程都必然相當昂貴。</span><span class="sxs-lookup"><span data-stu-id="c5cae-154">That coupling process, whether it involves instantiating a [Regex](xref:System.Text.RegularExpressions.Regex) object by passing its constructor a regular expression pattern or calling a static method by passing it the regular expression pattern along with the string to be analyzed, is by necessity an expensive one.</span></span>

<span data-ttu-id="c5cae-155">您可以結合規則運算式引擎與特定規則運算式模式，然後使用引擎透過數種方式比對文字：</span><span class="sxs-lookup"><span data-stu-id="c5cae-155">You can couple the regular expression engine with a particular regular expression pattern and then use the engine to match text in several ways:</span></span>

* <span data-ttu-id="c5cae-156">您可以呼叫靜態模式比對方法，例如 [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String))。</span><span class="sxs-lookup"><span data-stu-id="c5cae-156">You can call a static pattern-matching method, such as [Regex.Match(String, String)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String)).</span></span> <span data-ttu-id="c5cae-157">這樣就不需要具現化規則運算式物件。</span><span class="sxs-lookup"><span data-stu-id="c5cae-157">This does not require instantiation of a regular expression object.</span></span>

* <span data-ttu-id="c5cae-158">您可以具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件，並且呼叫解譯之規則運算式的執行個體模式比對方法。</span><span class="sxs-lookup"><span data-stu-id="c5cae-158">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of an interpreted regular expression.</span></span> <span data-ttu-id="c5cae-159">這是將規則運算式引擎繫結至規則運算式模式的預設方法。</span><span class="sxs-lookup"><span data-stu-id="c5cae-159">This is the default method for binding the regular expression engine to a regular expression pattern.</span></span> <span data-ttu-id="c5cae-160">這個方法會在 [Regex](xref:System.Text.RegularExpressions.Regex) 物件具現化，但是沒有包含 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 旗標的 options 引數時得出結果。</span><span class="sxs-lookup"><span data-stu-id="c5cae-160">It results when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated without an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

* <span data-ttu-id="c5cae-161">您可以具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件，並且呼叫編譯之規則運算式的執行個體模式比對方法。</span><span class="sxs-lookup"><span data-stu-id="c5cae-161">You can instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object and call an instance pattern-matching method of a compiled regular expression.</span></span> <span data-ttu-id="c5cae-162">當 [Regex](xref:System.Text.RegularExpressions.Regex) 物件具現化且包含 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 旗標的 options 引數時，規則運算式物件就會表示編譯的模式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-162">Regular expression objects represent compiled patterns when a [Regex](xref:System.Text.RegularExpressions.Regex) object is instantiated with an options argument that includes the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) flag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5cae-163">如果在方法呼叫中重複使用相同的規則運算式，或是應用程式大量使用規則運算式物件，則方法呼叫的形式 (靜態、解譯、編譯) 就會影響效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-163">The form of the method call (static, interpreted, compiled) affects performance if the same regular expression is used repeatedly in method calls, or if an application makes extensive use of regular expression objects.</span></span>
 
### <a name="static-regular-expressions"></a><span data-ttu-id="c5cae-164">靜態規則運算式</span><span class="sxs-lookup"><span data-stu-id="c5cae-164">Static regular expressions</span></span>

<span data-ttu-id="c5cae-165">建議您使用靜態規則運算式方法來替代使用相同的規則運算式重複具現化規則運算式物件。</span><span class="sxs-lookup"><span data-stu-id="c5cae-165">Static regular expression methods are recommended as an alternative to repeatedly instantiating a regular expression object with the same regular expression.</span></span> <span data-ttu-id="c5cae-166">與規則運算式物件所使用的規則運算式模式不同的是，規則運算式引擎會在內部快取作業程式碼或是從執行個體方法呼叫中所使用模式編譯的 Microsoft intermediate language (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-166">Unlike regular expression patterns used by regular expression objects, either the operation codes or the compiled Microsoft intermediate language (MSIL) from patterns used in instance method calls is cached internally by the regular expression engine.</span></span> 

<span data-ttu-id="c5cae-167">例如，您可以呼叫方法來驗證使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="c5cae-167">For example, you might call a method to validate user input.</span></span> <span data-ttu-id="c5cae-168">在此範例中，一個名為 `IsValidCurrency` 的方法會檢查使用者是否已輸入貨幣符號且後面至少有一個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-168">In this example, a method named `IsValidCurrency` checks whether the user has entered a currency symbol followed by at least one decimal digit.</span></span> <span data-ttu-id="c5cae-169">下列範例示範非常沒有效率的 `IsValidCurrency` 方法實作。</span><span class="sxs-lookup"><span data-stu-id="c5cae-169">A very inefficient implementation of the `IsValidCurrency` method is shown in the following example.</span></span> <span data-ttu-id="c5cae-170">請注意，每一個方法呼叫都會使用相同的模式重複具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件。</span><span class="sxs-lookup"><span data-stu-id="c5cae-170">Note that each method call reinstantiates a [Regex](xref:System.Text.RegularExpressions.Regex) object with the same pattern.</span></span> <span data-ttu-id="c5cae-171">而這表示，每次呼叫方法時都必須重新編譯規則運算式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-171">This, in turn, means that the regular expression pattern must be recompiled each time the method is called.</span></span>

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

<span data-ttu-id="c5cae-172">您應該用呼叫靜態 [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) 方法取代這個沒有效率的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5cae-172">You should replace this inefficient code with a call to the static [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) method.</span></span> <span data-ttu-id="c5cae-173">這樣就不必在每次您想要呼叫模式比對方法時具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件，並且可讓規則運算式引擎從其快取擷取編譯版的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-173">This eliminates the need to instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object each time you want to call a pattern-matching method, and enables the regular expression engine to retrieve a compiled version of the regular expression from its cache.</span></span>

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

<span data-ttu-id="c5cae-174">根據預設，會快取 15 個最近使用的靜態規則運算式模式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-174">By default, the last 15 most recently used static regular expression patterns are cached.</span></span> <span data-ttu-id="c5cae-175">針對需要大量快取之靜態規則運算式的應用程式，快取的大小可以透過設定 [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) 屬性加以調整。</span><span class="sxs-lookup"><span data-stu-id="c5cae-175">For applications that require a larger number of cached static regular expressions, the size of the cache can be adjusted by setting the [Regex.CacheSize](xref:System.Text.RegularExpressions.Regex.CacheSize) property.</span></span>

<span data-ttu-id="c5cae-176">這個範例中使用的規則運算式 `\p{Sc}+\s*\d+` 會驗證輸入字串是否包含貨幣符號和至少一個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-176">The regular expression `\p{Sc}+\s*\d+` that is used in this example verifies that the input string consists of a currency symbol and at least one decimal digit.</span></span> <span data-ttu-id="c5cae-177">模式的定義方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="c5cae-177">The pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="c5cae-178">模式</span><span class="sxs-lookup"><span data-stu-id="c5cae-178">Pattern</span></span> | <span data-ttu-id="c5cae-179">描述</span><span class="sxs-lookup"><span data-stu-id="c5cae-179">Description</span></span>
------- | -----------
`\p{Sc}+` | <span data-ttu-id="c5cae-180">比對 [Unicode Symbol, Currency] 分類中的一個或多個字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-180">Match one or more characters in the Unicode Symbol, Currency category.</span></span>
`\s*` | <span data-ttu-id="c5cae-181">比對零個以上的空白字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-181">Match zero or more white-space characters.</span></span>
`\d+` | <span data-ttu-id="c5cae-182">比對一個或多個十進位數字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-182">Match one or more decimal digits.</span></span>
 
### <a name="interpreted-vs-compiled-regular-expressions"></a><span data-ttu-id="c5cae-183">比較經過解譯與經過編譯的規則運算式</span><span class="sxs-lookup"><span data-stu-id="c5cae-183">Interpreted vs. compiled regular expressions</span></span>

<span data-ttu-id="c5cae-184">未透過指定 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項繫結至規則運算式引擎的規則運算式模式會加以解譯。</span><span class="sxs-lookup"><span data-stu-id="c5cae-184">Regular expression patterns that are not bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are interpreted.</span></span> <span data-ttu-id="c5cae-185">具現化規則運算式物件時，規則運算式引擎會將規則運算式轉換成一組作業程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5cae-185">When a regular expression object is instantiated, the regular expression engine converts the regular expression to a set of operation codes.</span></span> <span data-ttu-id="c5cae-186">呼叫執行個體方法時，作業程式碼會轉換成 MSIL 並且由 JIT 編譯器執行。</span><span class="sxs-lookup"><span data-stu-id="c5cae-186">When an instance method is called, the operation codes are converted to MSIL and executed by the JIT compiler.</span></span> <span data-ttu-id="c5cae-187">同樣地，當呼叫靜態規則運算式方法而快取中找不到規則運算式時，規則運算式引擎會將規則運算式轉換成一組作業程式碼，並且將它們儲存到快取中。</span><span class="sxs-lookup"><span data-stu-id="c5cae-187">Similarly, when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to a set of operation codes and stores them in the cache.</span></span> <span data-ttu-id="c5cae-188">然後引擎會將這些作業程式碼轉換成 MSIL，JIT 編譯器就可以執行這些作業程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5cae-188">It then converts these operation codes to MSIL so that the JIT compiler can execute them.</span></span> <span data-ttu-id="c5cae-189">解譯的規則運算式會藉由放慢執行時間來縮短啟動時間。</span><span class="sxs-lookup"><span data-stu-id="c5cae-189">Interpreted regular expressions reduce startup time at the cost of slower execution time.</span></span> <span data-ttu-id="c5cae-190">因此，在少數方法呼叫中使用規則運算式時，或是雖然不知道規則運算式方法呼叫的確實數目，但是期望數目很少時，最適合使用解譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-190">Because of this, they are best used when the regular expression is used in a small number of method calls, or if the exact number of calls to regular expression methods is unknown but is expected to be small.</span></span> <span data-ttu-id="c5cae-191">隨著方法呼叫的數目增加，放慢執行速度就會壓縮掉縮短啟動時間所獲得的效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-191">As the number of method calls increases, the performance gain from reduced startup time is outstripped by the slower execution speed.</span></span>

<span data-ttu-id="c5cae-192">透過指定 [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) 選項繫結至規則運算式引擎的規則運算式模式會加以編譯。</span><span class="sxs-lookup"><span data-stu-id="c5cae-192">Regular expression patterns that are bound to the regular expression engine through the specification of the [RegexOptions.Compiled](xref:System.Text.RegularExpressions.RegexOptions.Compiled) option are compiled.</span></span> <span data-ttu-id="c5cae-193">這表示，當具現化規則運算式物件，或是當呼叫靜態規則運算式方法而快取中找不到規則運算式時，規則運算式引擎會將規則運算式轉換成一組中繼的作業程式碼，然後將這些程式碼轉換成 MSIL。</span><span class="sxs-lookup"><span data-stu-id="c5cae-193">This means that, when a regular expression object is instantiated, or when a static regular expression method is called and the regular expression cannot be found in the cache, the regular expression engine converts the regular expression to an intermediary set of operation codes, which it then converts to MSIL.</span></span> <span data-ttu-id="c5cae-194">呼叫方法時，JIT 編譯器會執行 MSIL。</span><span class="sxs-lookup"><span data-stu-id="c5cae-194">When a method is called, the JIT compiler executes the MSIL.</span></span> <span data-ttu-id="c5cae-195">與解譯的規則運算式相反的是，編譯的規則運算式會延長啟動時間，但加快執行個別模式比對方法的速度。</span><span class="sxs-lookup"><span data-stu-id="c5cae-195">In contrast to interpreted regular expressions, compiled regular expressions increase startup time but execute individual pattern-matching methods faster.</span></span> <span data-ttu-id="c5cae-196">因此，編譯規則運算式所獲得的效能優勢會與呼叫的規則運算式方法數目成比例。</span><span class="sxs-lookup"><span data-stu-id="c5cae-196">As a result, the performance benefit that results from compiling the regular expression increases in proportion to the number of regular expression methods called.</span></span>

<span data-ttu-id="c5cae-197">簡言之，我們建議您在呼叫含有相對較不常用之特定規則運算式的規則運算式方法時，使用解譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-197">To summarize, we recommend that you use interpreted regular expressions when you call regular expression methods with a specific regular expression relatively infrequently.</span></span> <span data-ttu-id="c5cae-198">而當您呼叫含有相對較常用之特定規則運算式的規則運算式方法時，則應該使用編譯的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="c5cae-198">You should use compiled regular expressions when you call regular expression methods with a specific regular expression relatively frequently.</span></span> <span data-ttu-id="c5cae-199">無論是放慢解譯的規則運算式執行速度所提升的效能超過縮短的啟動時間，或是放慢編譯的規則運算式啟動時間所提升的效能超過加快執行速度，都不容易判斷出其確實的臨界值。</span><span class="sxs-lookup"><span data-stu-id="c5cae-199">The exact threshold at which the slower execution speeds of interpreted regular expressions outweigh gains from their reduced startup time, or the threshold at which the slower startup times of compiled regular expressions outweigh gains from their faster execution speeds, is difficult to determine.</span></span> <span data-ttu-id="c5cae-200">因為臨界值取決於各種不同的因素，包括規則運算式及其處理之特定資料的複雜度。</span><span class="sxs-lookup"><span data-stu-id="c5cae-200">It depends on a variety of factors, including the complexity of the regular expression and the specific data that it processes.</span></span> <span data-ttu-id="c5cae-201">若要判斷究竟是解譯或編譯的規則運算式能為您的特殊應用程式案例提供最佳效能，您可以使用 [Stopwatch](xref:System.Diagnostics.Stopwatch) 類別比較兩者的執行時間。</span><span class="sxs-lookup"><span data-stu-id="c5cae-201">To determine whether interpreted or compiled regular expressions offer the best performance for your particular application scenario, you can use the [Stopwatch](xref:System.Diagnostics.Stopwatch) class to compare their execution times.</span></span>

<span data-ttu-id="c5cae-202">下列範例會比較編譯和解譯的規則運算式讀取 Theodore Dreiser 所著 "The Financier" 一文的前十個句子及讀取所有句子時的效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-202">The following example compares the performance of compiled and interpreted regular expressions when reading the first ten sentences and when reading all the sentences in the text of Theodore Dreiser's The Financier.</span></span> <span data-ttu-id="c5cae-203">如範例的輸出所示，僅對規則運算式比對方法進行十次呼叫時，解譯的規則運算式能提供比編譯的規則運算式更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-203">As the output from the example shows, when only ten calls are made to regular expression matching methods, an interpreted regular expression offers better performance than a compiled regular expression.</span></span> <span data-ttu-id="c5cae-204">但是進行大量呼叫 (此案例中為超過 13,000 次) 時，編譯的規則運算式會提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-204">However, a compiled regular expression offers better performance when a large number of calls (in this case, over 13,000) are made.</span></span> 

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

<span data-ttu-id="c5cae-205">範例中所使用規則運算式模式 `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]` 的定義方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="c5cae-205">The regular expression pattern used in the example, `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, is defined as shown in the following table.</span></span>

<span data-ttu-id="c5cae-206">模式</span><span class="sxs-lookup"><span data-stu-id="c5cae-206">Pattern</span></span> | <span data-ttu-id="c5cae-207">描述</span><span class="sxs-lookup"><span data-stu-id="c5cae-207">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="c5cae-208">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="c5cae-208">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="c5cae-209">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-209">Match one or more word characters.</span></span>
<span data-ttu-id="c5cae-210">\`(\r?\n)</span><span class="sxs-lookup"><span data-stu-id="c5cae-210">\`(\r?\n)</span></span>|<span data-ttu-id="c5cae-211">,?\s)\`</span><span class="sxs-lookup"><span data-stu-id="c5cae-211">,?\s)\`</span></span> | <span data-ttu-id="c5cae-212">比對後面接著新行字元的零個或一個歸位字元，或是後面接著空白字元的零個或一個逗號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-212">Match either zero or one carriage return followed by a newline character, or zero or one comma followed by a white-space character.</span></span>
<span data-ttu-id="c5cae-213">\`(\w+((\r?\n)</span><span class="sxs-lookup"><span data-stu-id="c5cae-213">\`(\w+((\r?\n)</span></span>|<span data-ttu-id="c5cae-214">,?\s))*\`</span><span class="sxs-lookup"><span data-stu-id="c5cae-214">,?\s))*\`</span></span> | <span data-ttu-id="c5cae-215">比對出現零次或多次的一個或多個文字字元，其後面會接著零個或一個歸位字元和新行字元，或是後面接著空白字元的零個或一個逗號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-215">Match zero or more occurrences of one or more word characters that are followed either by zero or one carriage return and a newline character, or by zero or one comma followed by a white-space character.</span></span>
`\w+` | <span data-ttu-id="c5cae-216">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-216">Match one or more word characters.</span></span>
`[.?:;!]` | <span data-ttu-id="c5cae-217">比對句號、問號、冒號、分號或驚嘆號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-217">Match a period, question mark, colon, semicolon, or exclamation point.</span></span>
 
## <a name="take-charge-of-backtracking"></a><span data-ttu-id="c5cae-218">控制回溯</span><span class="sxs-lookup"><span data-stu-id="c5cae-218">Take charge of backtracking</span></span>

<span data-ttu-id="c5cae-219">通常規則運算式引擎會使用線性迴歸逐一處理輸入字串，並且與規則運算式模式比較。</span><span class="sxs-lookup"><span data-stu-id="c5cae-219">Ordinarily, the regular expression engine uses linear progression to move through an input string and compare it to a regular expression pattern.</span></span> <span data-ttu-id="c5cae-220">不過，當規則運算式模式中使用不定數的數量詞 (例如 __*__、**+** 和 **?**)</span><span class="sxs-lookup"><span data-stu-id="c5cae-220">However, when indeterminate quantifiers such as __*__, **+**, and **?**</span></span> <span data-ttu-id="c5cae-221">時，規則運算式引擎可能會放棄一部分成功的部分符合結果，並且返回之前儲存的狀態，以便搜尋與整個模式完全相符的結果。</span><span class="sxs-lookup"><span data-stu-id="c5cae-221">are used in a regular expression pattern, the regular expression engine may give up a portion of successful partial matches and return to a previously saved state in order to search for a successful match for the entire pattern.</span></span> <span data-ttu-id="c5cae-222">這個程序稱為「回溯」(Backtracking)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-222">This process is known as backtracking.</span></span>

> [!NOTE]
> <span data-ttu-id="c5cae-223">如需回溯的詳細資訊，請參閱[規則運算式行為的詳細資料](regex-behavior.md)及[規則運算式中的回溯](backtracking.md)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-223">For more information on backtracking, see [Details of regular expression behavior](regex-behavior.md) and [Backtracking in regular expressions](backtracking.md).</span></span>
 
<span data-ttu-id="c5cae-224">支援回溯能讓規則運算式更強大且更靈活，</span><span class="sxs-lookup"><span data-stu-id="c5cae-224">Support for backtracking gives regular expressions power and flexibility.</span></span> <span data-ttu-id="c5cae-225">同時還能讓規則運算式開發人員負責掌控規則運算式引擎的作業。</span><span class="sxs-lookup"><span data-stu-id="c5cae-225">It also places the responsibility for controlling the operation of the regular expression engine in the hands of regular expression developers.</span></span> <span data-ttu-id="c5cae-226">由於開發人員經常忽略這個責任而誤用回溯或大量使用回溯，因而時常是造成規則運算式效能低落的最重要原因。</span><span class="sxs-lookup"><span data-stu-id="c5cae-226">Because developers are often not aware of this responsibility, their misuse of backtracking or reliance on excessive backtracking often plays the most significant role in degrading regular expression performance.</span></span> <span data-ttu-id="c5cae-227">在最糟的情況下，輸入字串中每個超出字元的執行時間可能會倍增。</span><span class="sxs-lookup"><span data-stu-id="c5cae-227">In a worst-case scenario, execution time can double for each additional character in the input string.</span></span> <span data-ttu-id="c5cae-228">事實上，如果輸入幾乎符合規則運算式模式的話，大量使用回溯很容易製造相當於程式設計上的無窮迴圈，而規則運算式引擎可能需要數小時，甚至數天來處理相對來說很短的輸入字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-228">In fact, by using backtracking excessively, it is easy to create the programmatic equivalent of an endless loop if input nearly matches the regular expression pattern; the regular expression engine may take hours or even days to process a relatively short input string.</span></span>

<span data-ttu-id="c5cae-229">儘管回溯並不是比對的要件，應用程式常常會因為使用回溯而影響效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-229">Often, applications pay a performance penalty for using backtracking despite the fact that backtracking is not essential for a match.</span></span> <span data-ttu-id="c5cae-230">例如，規則運算式 `\b\p{Lu}\w*\b` 會比對所有開頭為大寫字元的文字，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="c5cae-230">For example, the regular expression `\b\p{Lu}\w*\b` matches all words that begin with an uppercase character, as the following table shows.</span></span>

<span data-ttu-id="c5cae-231">模式</span><span class="sxs-lookup"><span data-stu-id="c5cae-231">Pattern</span></span> | <span data-ttu-id="c5cae-232">描述</span><span class="sxs-lookup"><span data-stu-id="c5cae-232">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="c5cae-233">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="c5cae-233">Begin the match at a word boundary.</span></span>
`\p{Lu}` | <span data-ttu-id="c5cae-234">比對大寫字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-234">Match an uppercase character.</span></span>
`\w*` | <span data-ttu-id="c5cae-235">比對零個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-235">Match zero or more word characters.</span></span>
`\b` | <span data-ttu-id="c5cae-236">結束字緣比對。</span><span class="sxs-lookup"><span data-stu-id="c5cae-236">End the match at a word boundary.</span></span>
 
<span data-ttu-id="c5cae-237">由於字緣與文字字元不同，也不是文字字元的子集，因此規則運算式引擎不可能在比對文字字元時跨越字緣。</span><span class="sxs-lookup"><span data-stu-id="c5cae-237">Because a word boundary is not the same as, or a subset of, a word character, there is no possibility that the regular expression engine will cross a word boundary when matching word characters.</span></span> <span data-ttu-id="c5cae-238">這表示對於這個規則運算式來說，回溯不會使任何比對完全成功，只會造成效能降低，因為規則運算式引擎會被迫儲存每一個成功的初始文字字元比對的狀態。</span><span class="sxs-lookup"><span data-stu-id="c5cae-238">This means that for this regular expression, backtracking can never contribute to the overall success of any match -- it can only degrade performance, because the regular expression engine is forced to save its state for each successful preliminary match of a word character.</span></span>

<span data-ttu-id="c5cae-239">如果您判定不需要回溯，可以使用 **(?>**_subexpression_**)** 語言項目將它停用。</span><span class="sxs-lookup"><span data-stu-id="c5cae-239">If you determine that backtracking is not necessary, you can disable it by using the **(?>**_subexpression_**)** language element.</span></span> <span data-ttu-id="c5cae-240">下列範例會使用兩個規則運算式剖析輸入字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-240">The following example parses an input string by using two regular expressions.</span></span> <span data-ttu-id="c5cae-241">首先，`\b\p{Lu}\w*\b` 會仰賴回溯。</span><span class="sxs-lookup"><span data-stu-id="c5cae-241">The first, `\b\p{Lu}\w*\b`, relies on backtracking.</span></span> <span data-ttu-id="c5cae-242">第二，`\b\p{Lu}(?>\w*)\b` 會停用回溯。</span><span class="sxs-lookup"><span data-stu-id="c5cae-242">The second, `\b\p{Lu}(?>\w*)\b`, disables backtracking.</span></span> <span data-ttu-id="c5cae-243">如範例的輸出所示，兩者會產生相同的結果。</span><span class="sxs-lookup"><span data-stu-id="c5cae-243">As the output from the example shows, they both produce the same result.</span></span>

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

<span data-ttu-id="c5cae-244">在許多情況下，回溯是比對規則運算式模式與輸入文字時所必要。</span><span class="sxs-lookup"><span data-stu-id="c5cae-244">In many cases, backtracking is essential for matching a regular expression pattern to input text.</span></span> <span data-ttu-id="c5cae-245">不過，大量回溯可能嚴重降低效能，並且製造應用程式停止回應的印象。</span><span class="sxs-lookup"><span data-stu-id="c5cae-245">However, excessive backtracking can severely degrade performance and create the impression that an application has stopped responding.</span></span> <span data-ttu-id="c5cae-246">尤其是當數量詞為巢狀，而且符合外部子運算式的文字是符合內部子運算式之文字的子集時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="c5cae-246">In particular, this happens when quantifiers are nested and the text that matches the outer subexpression is a subset of the text that matches the inner subexpression.</span></span> 

> [!WARNING]
> <span data-ttu-id="c5cae-247">除了避免大量回溯以外，您應該使用逾時功能確保大量回溯不會嚴重降低規則運算式的效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-247">In addition to avoiding excessive backtracking, you should use the timeout feature to ensure that excessive backtracking does not severely degrade regular expression performance.</span></span> <span data-ttu-id="c5cae-248">如需詳細資訊，請參閱[使用逾時值](#use-time-out-values)一節。</span><span class="sxs-lookup"><span data-stu-id="c5cae-248">For more information, see the [Use time-out values](#use-time-out-values) section.</span></span>
 
<span data-ttu-id="c5cae-249">例如，規則運算式模式 `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` 的目的在於比對至少包含一個英數字元的零件編號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-249">For example, the regular expression pattern `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` is intended to match a part number that consists of at least one alphanumeric character.</span></span> <span data-ttu-id="c5cae-250">任何額外的字元都可能包含英數字元、連字號、底線或句號，不過最後一個字元必須是英數字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-250">Any additional characters can consist of an alphanumeric character, a hyphen, an underscore, or a period, though the last character must be alphanumeric.</span></span> <span data-ttu-id="c5cae-251">$ 符號則結束零件編號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-251">A dollar sign terminates the part number.</span></span> <span data-ttu-id="c5cae-252">在某些情況下，這個規則運算式模式可能顯現出極差的效能，因為數量詞為巢狀，而且子運算式 `[0-9A-Z]` 是 `[-.\w]*` 子運算式的子集。</span><span class="sxs-lookup"><span data-stu-id="c5cae-252">In some cases, this regular expression pattern can exhibit extremely poor performance because quantifiers are nested, and because the subexpression `[0-9A-Z]` is a subset of the subexpression `[-.\w]*`.</span></span>

<span data-ttu-id="c5cae-253">在這類情況下，您可以移除巢狀數量詞，並且將外部子運算式取代為零寬度的右合樣或左合樣判斷提示，藉此最佳化規則運算式的效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-253">In these cases, you can optimize regular expression performance by removing the nested quantifiers and replacing the outer subexpression with a zero-width lookahead or lookbehind assertion.</span></span> <span data-ttu-id="c5cae-254">右合樣和左合樣判斷提示是錨點，它們不會移動輸入字串中的指標，而是向右或向左合樣，以檢查是否符合指定的條件。</span><span class="sxs-lookup"><span data-stu-id="c5cae-254">Lookahead and lookbehind assertions are anchors; they do not move the pointer in the input string, but instead look ahead or behind to check whether a specified condition is met.</span></span> <span data-ttu-id="c5cae-255">例如，零件編號規則運算式可以重寫為 `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`。</span><span class="sxs-lookup"><span data-stu-id="c5cae-255">For example, the part number regular expression can be rewritten as `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`.</span></span> <span data-ttu-id="c5cae-256">這個規則運算式模式的定義方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="c5cae-256">This regular expression pattern is defined as shown in the following table.</span></span>

<span data-ttu-id="c5cae-257">模式</span><span class="sxs-lookup"><span data-stu-id="c5cae-257">Pattern</span></span> | <span data-ttu-id="c5cae-258">描述</span><span class="sxs-lookup"><span data-stu-id="c5cae-258">Description</span></span>
------- | -----------
`^` | <span data-ttu-id="c5cae-259">在輸入字串的開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="c5cae-259">Begin the match at the beginning of the input string.</span></span>
`[0-9A-Z]` | <span data-ttu-id="c5cae-260">比對英數字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-260">Match an alphanumeric character.</span></span> <span data-ttu-id="c5cae-261">零件編號必須至少包含這個字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-261">The part number must consist of at least this character.</span></span>
`[-.\w]*` | <span data-ttu-id="c5cae-262">比對出現零次或多次的任何文字字元、連字號或句號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-262">Match zero or more occurrences of any word character, hyphen, or period.</span></span>
<span data-ttu-id="c5cae-263">\`\$]</span><span class="sxs-lookup"><span data-stu-id="c5cae-263">\`\$]</span></span> | <span data-ttu-id="c5cae-264">比對 $ 符號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-264">Match a dollar sign.</span></span>
`(?<=[0-9A-Z])` | <span data-ttu-id="c5cae-265">向右合樣結尾的 $ 符號，確定前一個字元是英數字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-265">Look ahead of the ending dollar sign to ensure that the previous character is alphanumeric.</span></span>
<span data-ttu-id="c5cae-266">`$` 在輸入字串結尾時結束比對。</span><span class="sxs-lookup"><span data-stu-id="c5cae-266">`$` End the match at the end of the input string.</span></span>
 
<span data-ttu-id="c5cae-267">下列範例說明如何使用這個規則運算式比對包含可能零件編號的陣列。</span><span class="sxs-lookup"><span data-stu-id="c5cae-267">The following example illustrates the use of this regular expression to match an array containing possible part numbers.</span></span>

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

<span data-ttu-id="c5cae-268">.NET 中的規則運算式語言包括下列語言項目，可讓您用來消除巢狀數量詞。</span><span class="sxs-lookup"><span data-stu-id="c5cae-268">The regular expression language in .NET includes the following language elements that you can use to eliminate nested quantifiers.</span></span> <span data-ttu-id="c5cae-269">如需詳細資訊，請參閱[規則運算式中的群組建構](grouping.md)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-269">For more information, see [Grouping constructs in regular expressions](grouping.md).</span></span>

<span data-ttu-id="c5cae-270">語言項目</span><span class="sxs-lookup"><span data-stu-id="c5cae-270">Language element</span></span> | <span data-ttu-id="c5cae-271">描述</span><span class="sxs-lookup"><span data-stu-id="c5cae-271">Description</span></span>
---------------- | ----------- 
<span data-ttu-id="c5cae-272">**(?**=_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="c5cae-272">**(?**=_subexpression_**)**</span></span> | <span data-ttu-id="c5cae-273">零寬度右合樣。</span><span class="sxs-lookup"><span data-stu-id="c5cae-273">Zero-width positive lookahead.</span></span> <span data-ttu-id="c5cae-274">從目前的位置向右合樣，判斷 *subexpression* 是否符合輸入字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-274">Look ahead of the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="c5cae-275">**(?!**_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="c5cae-275">**(?!**_subexpression_**)**</span></span> | <span data-ttu-id="c5cae-276">零寬度右不合樣。</span><span class="sxs-lookup"><span data-stu-id="c5cae-276">Zero-width negative lookahead.</span></span> <span data-ttu-id="c5cae-277">從目前的位置向右合樣，判斷 *subexpression* 是否不符合輸入字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-277">Look ahead of the current position to determine whether *subexpression* does not match the input string.</span></span>
<span data-ttu-id="c5cae-278">**(?<**=_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="c5cae-278">**(?<**=_subexpression_**)**</span></span> | <span data-ttu-id="c5cae-279">零寬度左合樣。</span><span class="sxs-lookup"><span data-stu-id="c5cae-279">Zero-width positive lookbehind.</span></span> <span data-ttu-id="c5cae-280">從目前的位置向左合樣，判斷 *subexpression* 是否符合輸入字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-280">Look behind the current position to determine whether *subexpression* matches the input string.</span></span>
<span data-ttu-id="c5cae-281">**(?<!**_subexpression_**)**</span><span class="sxs-lookup"><span data-stu-id="c5cae-281">**(?<!**_subexpression_**)**</span></span> | <span data-ttu-id="c5cae-282">零寬度左不合樣。</span><span class="sxs-lookup"><span data-stu-id="c5cae-282">Zero-width negative lookbehind.</span></span> <span data-ttu-id="c5cae-283">從目前的位置向左合樣，判斷 *subexpression* 是否不符合輸入字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-283">Look behind the current position to determine whether *subexpression* does not match the input string.</span></span>
 
## <a name="use-time-out-values"></a><span data-ttu-id="c5cae-284">使用逾時值</span><span class="sxs-lookup"><span data-stu-id="c5cae-284">Use time-out values</span></span>

<span data-ttu-id="c5cae-285">如果您的規則運算式會處理幾乎符合規則運算式模式的輸入，它經常會依賴大量回溯，如此就會大幅影響其效能。</span><span class="sxs-lookup"><span data-stu-id="c5cae-285">If your regular expressions processes input that nearly matches the regular expression pattern, it can often rely on excessive backtracking, which impacts its performance significantly.</span></span> <span data-ttu-id="c5cae-286">除了仔細考量使用回溯以及對幾乎符合的輸入進行規則運算式測試之外，務必要設定逾時值，以確保將大量回溯 (如發生的話) 的影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="c5cae-286">In addition to carefully considering your use of backtracking and testing the regular expression against near-matching input, you should always set a time-out value to ensure that the impact of excessive backtracking, if it occurs, is minimized.</span></span>

<span data-ttu-id="c5cae-287">規則運算式逾時間隔會定義規則運算式引擎在逾時前，將尋找單一相符項目的一段時間。</span><span class="sxs-lookup"><span data-stu-id="c5cae-287">The regular expression time-out interval defines the period of time that the regular expression engine will look for a single match before it times out.</span></span> <span data-ttu-id="c5cae-288">預設的逾時間隔是 [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout)，這表示規則運算式不會逾時。</span><span class="sxs-lookup"><span data-stu-id="c5cae-288">The default time-out interval is [Regex.InfiniteMatchTimeout](xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout), which means that the regular expression will not time out.</span></span> <span data-ttu-id="c5cae-289">您可以依照下述方式覆寫這個值並定義逾時間隔：</span><span class="sxs-lookup"><span data-stu-id="c5cae-289">You can override this value and define a time-out interval as follows:</span></span> 

* <span data-ttu-id="c5cae-290">在您呼叫 [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) 建構函式具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件時提供逾時值。</span><span class="sxs-lookup"><span data-stu-id="c5cae-290">By providing a time-out value when you instantiate a [Regex](xref:System.Text.RegularExpressions.Regex) object by calling the [Regex(String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.%23ctor(System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) constructor.</span></span>

* <span data-ttu-id="c5cae-291">呼叫靜態模式比對方法，例如，包含 *matchTimeout* 參數的 [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) 或 [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan))。</span><span class="sxs-lookup"><span data-stu-id="c5cae-291">By calling a static pattern matching method, such as [Regex.Match(String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Match(System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)) or [Regex.Replace(String, String, String, RegexOptions, TimeSpan)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.String,System.Text.RegularExpressions.RegexOptions,System.TimeSpan)), that includes a *matchTimeout* parameter.</span></span>

<span data-ttu-id="c5cae-292">如果您已定義逾時間隔，但是在該間隔結束時未找到相符項目，則規則運算式方法會擲回 [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c5cae-292">If you have defined a time-out interval and a match is not found at the end of that interval, the regular expression method throws a [RegexMatchTimeoutException](xref:System.Text.RegularExpressions.RegexMatchTimeoutException) exception.</span></span> <span data-ttu-id="c5cae-293">在例外處理常式中，您可以選擇以較長的逾時間隔重試比對、放棄比對嘗試並假設沒有相符項目，或是放棄比對嘗試並記錄例外狀況資訊供未來進行分析。</span><span class="sxs-lookup"><span data-stu-id="c5cae-293">In your exception handler, you can choose to retry the match with a longer time-out interval, abandon the match attempt and assume that there is no match, or abandon the match attempt and log the exception information for future analysis.</span></span>

<span data-ttu-id="c5cae-294">下列範例將定義 `GetWordData` 方法，該方法會具現化逾時間隔為 350 毫秒的規則運算式，以計算文字文件中的字數和一個字的平均字元數。</span><span class="sxs-lookup"><span data-stu-id="c5cae-294">The following example defines a `GetWordData` method that instantiates a regular expression with a time-out interval of 350 milliseconds to calculate the number of words and average number of characters in a word in a text document.</span></span> <span data-ttu-id="c5cae-295">如果比對作業逾時，則逾時間隔將增加 350 毫秒，並且重新具現化 [Regex](xref:System.Text.RegularExpressions.Regex) 物件。</span><span class="sxs-lookup"><span data-stu-id="c5cae-295">If the matching operation times out, the time-out interval is increased by 350 milliseconds and the [Regex](xref:System.Text.RegularExpressions.Regex) object is re-instantiated.</span></span> <span data-ttu-id="c5cae-296">如果新的逾時間隔超過 1 秒，則方法會重新擲回例外狀況至呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c5cae-296">If the new time-out interval exceeds 1 second, the method re-throws the exception to the caller.</span></span>

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

## <a name="capture-only-when-necessary"></a><span data-ttu-id="c5cae-297">必要時擷取</span><span class="sxs-lookup"><span data-stu-id="c5cae-297">Capture only when necessary</span></span>

<span data-ttu-id="c5cae-298">.NET 中的規則運算式支援許多群組建構，可讓您將規則運算式模式與一或多個子運算式設為群組。</span><span class="sxs-lookup"><span data-stu-id="c5cae-298">Regular expressions in .NET support a number of grouping constructs, which let you group a regular expression pattern into one or more subexpressions.</span></span> <span data-ttu-id="c5cae-299">.NET 規則運算式語言中最常用的群組建構為 **(**_subexpression_**)** (用於定義編號擷取群組) 和 **(?<*_name_**>**_subexpression_**)** (用於定義具名擷取群組)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-299">The most commonly used grouping constructs in .NET regular expression language are **(**_subexpression_**)**, which defines a numbered capturing group, and **(?<*_name_**>**_subexpression_**)**, which defines a named capturing group.</span></span> <span data-ttu-id="c5cae-300">群組建構是建立反向參考和定義套用數量詞之子運算式的要件。</span><span class="sxs-lookup"><span data-stu-id="c5cae-300">Grouping constructs are essential for creating backreferences and for defining a subexpression to which a quantifier is applied.</span></span> 

<span data-ttu-id="c5cae-301">不過，使用這些語言項目也有其代價。</span><span class="sxs-lookup"><span data-stu-id="c5cae-301">However, the use of these language elements has a cost.</span></span> <span data-ttu-id="c5cae-302">這些語言項目會造成在 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 屬性傳回的 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 物件中填入最近使用的未命名或具名擷取，而如果單一群組建構擷取了輸入字串中的多個子字串，則這些語言項目也會在特定擷取群組的 [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) 屬性傳回的 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件中填入多個 [Capture](xref:System.Text.RegularExpressions.Capture) 物件。</span><span class="sxs-lookup"><span data-stu-id="c5cae-302">They cause the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) object returned by the [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) property to be populated with the most recent unnamed or named captures, and if a single grouping construct has captured multiple substrings in the input string, they also populate the [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) object returned by the [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) property of a particular capturing group with multiple [Capture](xref:System.Text.RegularExpressions.Capture) objects.</span></span>

<span data-ttu-id="c5cae-303">通常在規則運算式中使用群組建構的目的在於能夠套用數量詞，而且後續不會使用這些子運算式擷取的群組。</span><span class="sxs-lookup"><span data-stu-id="c5cae-303">Often, grouping constructs are used in a regular expression only so that quantifiers can be applied to them, and the groups captured by these subexpressions are not subsequently used.</span></span> <span data-ttu-id="c5cae-304">例如，規則運算式 `\b(\w+[;,]?\s?)+[.?!]` 是設計用來擷取整個句子。</span><span class="sxs-lookup"><span data-stu-id="c5cae-304">For example, the regular expression `\b(\w+[;,]?\s?)+[.?!]` is designed to capture an entire sentence.</span></span> <span data-ttu-id="c5cae-305">下表描述這個規則運算式模式中的語言項目，及其對於 [Match](xref:System.Text.RegularExpressions.Match) 物件的 [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) 和 [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) 集合造成的影響。</span><span class="sxs-lookup"><span data-stu-id="c5cae-305">The following table describes the language elements in this regular expression pattern and their effect on the [Match](xref:System.Text.RegularExpressions.Match) object's [Match.Groups](xref:System.Text.RegularExpressions.Match.Groups) and [Group.Captures](xref:System.Text.RegularExpressions.Group.Captures) collections.</span></span>

<span data-ttu-id="c5cae-306">模式</span><span class="sxs-lookup"><span data-stu-id="c5cae-306">Pattern</span></span> | <span data-ttu-id="c5cae-307">描述</span><span class="sxs-lookup"><span data-stu-id="c5cae-307">Description</span></span>
------- | -----------
`\b` | <span data-ttu-id="c5cae-308">開始字緣比對。</span><span class="sxs-lookup"><span data-stu-id="c5cae-308">Begin the match at a word boundary.</span></span>
`\w+` | <span data-ttu-id="c5cae-309">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-309">Match one or more word characters.</span></span>
`[;,]?` | <span data-ttu-id="c5cae-310">比對零個或一個逗號或分號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-310">Match zero or one comma or semicolon.</span></span>
`\s?` | <span data-ttu-id="c5cae-311">比對零個或一個空白字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-311">Match zero or one white-space character.</span></span>
`(\w+[;,]?\s?)+` | <span data-ttu-id="c5cae-312">比對出現一次或多次的一個或多個文字字元，後面接著選擇性的逗號或分號，再後面接著選擇性的空白字元。</span><span class="sxs-lookup"><span data-stu-id="c5cae-312">Match one or more occurrences of one or more word characters followed by an optional comma or semicolon followed by an optional white-space character.</span></span> <span data-ttu-id="c5cae-313">這會定義必要的第一個擷取群組，如此多個文字字元 (也就是文字) 後面接著選擇性標點符號的組合才會重複，直到規則運算式引擎到達句尾為止。</span><span class="sxs-lookup"><span data-stu-id="c5cae-313">This defines the first capturing group, which is necessary so that the combination of multiple word characters (that is, a word) followed by an optional punctuation symbol will be repeated until the regular expression engine reaches the end of a sentence.</span></span>
`[.?!]` | <span data-ttu-id="c5cae-314">比對句號、問號或驚嘆號。</span><span class="sxs-lookup"><span data-stu-id="c5cae-314">Match a period, question mark, or exclamation point.</span></span>
 
<span data-ttu-id="c5cae-315">如下列範例所示，找到符合的結果時，[GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 和 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 物件中都會填入比對所擷取的項目。</span><span class="sxs-lookup"><span data-stu-id="c5cae-315">As the following example shows, when a match is found, both the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) objects are populated with captures from the match.</span></span> <span data-ttu-id="c5cae-316">在此案例中，擷取群組 `(\w+[;,]?\s?)` 會存在，如此 **+** 數量詞就能套用至其中，這樣就能讓規則運算式模式比對句子中的每個字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-316">In this case, the capturing group `(\w+[;,]?\s?)` exists so that the **+** quantifier can be applied to it, which enables the regular expression pattern to match each word in a sentence.</span></span> <span data-ttu-id="c5cae-317">否則就會比對句子中的最後一個字。</span><span class="sxs-lookup"><span data-stu-id="c5cae-317">Otherwise, it would match the last word in a sentence.</span></span>

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

<span data-ttu-id="c5cae-318">如果您使用子運算式的目的只是要在其中套用數量詞，對於擷取的文字並不感興趣，則應該停用群組擷取。</span><span class="sxs-lookup"><span data-stu-id="c5cae-318">When you use subexpressions only to apply quantifiers to them, and you are not interested in the captured text, you should disable group captures.</span></span> <span data-ttu-id="c5cae-319">例如，**(?:**_subexpression_**)** 語言項目會阻止套用該語言項目的群組擷取相符的子字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-319">For example, the **(?:**_subexpression_**)** language element prevents the group to which it applies from capturing matched substrings.</span></span> <span data-ttu-id="c5cae-320">在下列範例中，前一個範例的規則運算式模式會變成 `\b(?:\w+[;,]?\s?)+[.?!]`。</span><span class="sxs-lookup"><span data-stu-id="c5cae-320">In the following example, the regular expression pattern from the previous example is changed to `\b(?:\w+[;,]?\s?)+[.?!]`.</span></span> <span data-ttu-id="c5cae-321">如輸出所示，它會阻止規則運算式引擎填入 [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) 和 [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) 集合。</span><span class="sxs-lookup"><span data-stu-id="c5cae-321">As the output shows, it prevents the regular expression engine from populating the [GroupCollection](xref:System.Text.RegularExpressions.GroupCollection) and [CaptureCollection](xref:System.Text.RegularExpressions.CaptureCollection) collections.</span></span>

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

<span data-ttu-id="c5cae-322">您可以透過下列其中一種方式停用擷取：</span><span class="sxs-lookup"><span data-stu-id="c5cae-322">You can disable captures in one of the following ways:</span></span>

* <span data-ttu-id="c5cae-323">使用 **(?:**_subexpression_**)** 語言項目。</span><span class="sxs-lookup"><span data-stu-id="c5cae-323">Use the **(?:**_subexpression_**)** language element.</span></span> <span data-ttu-id="c5cae-324">這個項目會阻止在套用該項目的群組中擷取相符的子字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-324">This element prevents the capture of matched substrings in the group to which it applies.</span></span> <span data-ttu-id="c5cae-325">不過，它不會停用任何巢狀群組中的子字串擷取。</span><span class="sxs-lookup"><span data-stu-id="c5cae-325">It does not disable substring captures in any nested groups.</span></span>

* <span data-ttu-id="c5cae-326">使用 [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) 選項。</span><span class="sxs-lookup"><span data-stu-id="c5cae-326">Use the [RegexOptions.ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) option.</span></span> <span data-ttu-id="c5cae-327">這個選項會停用規則運算式模式中的所有未命名或隱含擷取。</span><span class="sxs-lookup"><span data-stu-id="c5cae-327">It disables all unnamed or implicit captures in the regular expression pattern.</span></span> <span data-ttu-id="c5cae-328">當您使用這個選項時，只會擷取符合 **(?<**_name_**>**_subexpression_**)** 語言項目所定義之具名群組的子字串。</span><span class="sxs-lookup"><span data-stu-id="c5cae-328">When you use this option, only substrings that match named groups defined with the **(?<**_name_**>**_subexpression_**)** language element can be captured.</span></span> <span data-ttu-id="c5cae-329">[ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) 旗標可以傳遞至 [Regex](xref:System.Text.RegularExpressions.Regex)類別建構函式的 options 參數，或是 [Regex](xref:System.Text.RegularExpressions.Regex) 靜態比對方法的 options 參數。</span><span class="sxs-lookup"><span data-stu-id="c5cae-329">The [ExplicitCapture](xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture) flag can be passed to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) class constructor or to the options parameter of a [Regex](xref:System.Text.RegularExpressions.Regex) static matching method.</span></span>

* <span data-ttu-id="c5cae-330">在 **(?imnsx)** 語言項目中使用 **n** 選項。</span><span class="sxs-lookup"><span data-stu-id="c5cae-330">Use the **n** option in the **(?imnsx)** language element.</span></span> <span data-ttu-id="c5cae-331">這個選項會從規則運算式模式中出現該項目的位置開始，停用所有未命名或隱含擷取。</span><span class="sxs-lookup"><span data-stu-id="c5cae-331">This option disables all unnamed or implicit captures from the point in the regular expression pattern at which the element appears.</span></span> <span data-ttu-id="c5cae-332">在到達模式結尾或 **(-n)** 選項啟用未命名或隱含擷取之前，擷取都會是停用狀態。</span><span class="sxs-lookup"><span data-stu-id="c5cae-332">Captures are disabled either until the end of the pattern or until the **(-n)** option enables unnamed or implicit captures.</span></span> <span data-ttu-id="c5cae-333">如需詳細資訊，請參閱[規則運算式中的其他建構](miscellaneous.md)。</span><span class="sxs-lookup"><span data-stu-id="c5cae-333">For more information, see [Miscellaneous constructs in regular expressions](miscellaneous.md).</span></span>

* <span data-ttu-id="c5cae-334">在 **(?imnsx:**_subexpression_**)** 語言項目中使用 **n** 選項。</span><span class="sxs-lookup"><span data-stu-id="c5cae-334">Use the **n** option in the **(?imnsx:**_subexpression_**)** language element.</span></span> <span data-ttu-id="c5cae-335">這個選項會停用 *subexpression* 中的所有未命名或隱含擷取。</span><span class="sxs-lookup"><span data-stu-id="c5cae-335">This option disables all unnamed or implicit captures in *subexpression*.</span></span> <span data-ttu-id="c5cae-336">任何未命名或隱含巢狀擷取群組所進行的擷取也都會停用。</span><span class="sxs-lookup"><span data-stu-id="c5cae-336">Captures by any unnamed or implicit nested capturing groups are disabled as well.</span></span>

## <a name="related-topics"></a><span data-ttu-id="c5cae-337">相關主題</span><span class="sxs-lookup"><span data-stu-id="c5cae-337">Related topics</span></span>

<span data-ttu-id="c5cae-338">標題</span><span class="sxs-lookup"><span data-stu-id="c5cae-338">Title</span></span> | <span data-ttu-id="c5cae-339">說明</span><span class="sxs-lookup"><span data-stu-id="c5cae-339">Description</span></span>
----- | ----------- 
[<span data-ttu-id="c5cae-340">規則運算式行為的詳細資料</span><span class="sxs-lookup"><span data-stu-id="c5cae-340">Details of regular expression behavior</span></span>](regex-behavior.md) | <span data-ttu-id="c5cae-341">檢查 .NET 中規則運算式引擎的實作。</span><span class="sxs-lookup"><span data-stu-id="c5cae-341">Examines the implementation of the regular expression engine in .NET.</span></span> <span data-ttu-id="c5cae-342">本主題將強調規則運算式的靈活度，並且說明開發人員應負責確保規則運算式引擎有效率且穩定地運作。</span><span class="sxs-lookup"><span data-stu-id="c5cae-342">The topic focuses on the flexibility of regular expressions and explains the developer's responsibility for ensuring the efficient and robust operation of the regular expression engine.</span></span>
[<span data-ttu-id="c5cae-343">規則運算式中的回溯</span><span class="sxs-lookup"><span data-stu-id="c5cae-343">Backtracking in regular expressions</span></span>](backtracking.md) | <span data-ttu-id="c5cae-344">說明何謂回溯以及回溯如何影響規則運算式的效能，並且檢查提供回溯之替代方式的語言項目。</span><span class="sxs-lookup"><span data-stu-id="c5cae-344">Explains what backtracking is and how it affects regular expression performance, and examines language elements that provide alternatives to backtracking.</span></span>
[<span data-ttu-id="c5cae-345">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="c5cae-345">Regular expression language - quick reference</span></span>](quick-ref.md) | <span data-ttu-id="c5cae-346">描述 .NET 中規則運算式語言的項目，並且提供每個語言項目之詳細文件的連結。</span><span class="sxs-lookup"><span data-stu-id="c5cae-346">Describes the elements of the regular expression language in .NET and provides links to detailed documentation for each language element.</span></span>
 



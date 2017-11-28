---
title: "如何：使用 String.Split 剖析字串 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="30d7a-102">如何：使用 String.Split 剖析字串 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="30d7a-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="30d7a-103">下列程式碼範例示範如何使用 <xref:System.String.Split%2A?displayProperty=nameWithType> 方法剖析字串。</span><span class="sxs-lookup"><span data-stu-id="30d7a-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="30d7a-104">當輸入時， <xref:System.String.Split%2A> 會採用字元陣列以表示用來分隔目標字串之有趣子字串的字元。</span><span class="sxs-lookup"><span data-stu-id="30d7a-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="30d7a-105">該函式會傳回子字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="30d7a-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="30d7a-106">這個範例會使用空格、逗號、句號、冒號和定位點，全部以包含這些分隔符號的陣列傳遞至 <xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="30d7a-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="30d7a-107">目標字串句子中的每個文字都會使用字串結果陣列來個別顯示。</span><span class="sxs-lookup"><span data-stu-id="30d7a-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30d7a-108">範例</span><span class="sxs-lookup"><span data-stu-id="30d7a-108">Example</span></span>  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="30d7a-109">範例</span><span class="sxs-lookup"><span data-stu-id="30d7a-109">Example</span></span>  
 <span data-ttu-id="30d7a-110">根據預設，當目標字串中連續出現兩個分隔字元時，String.Split 會傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="30d7a-110">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="30d7a-111">您可以傳遞選擇性 StringSplitOptions.RemoveEmptyEntries 參數，以排除輸出中的任何空字串。</span><span class="sxs-lookup"><span data-stu-id="30d7a-111">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="30d7a-112">String.Split 可採用字串陣列 (做為分隔符號以剖析目標字串的字元序列，而不是單一字元)。</span><span class="sxs-lookup"><span data-stu-id="30d7a-112">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="30d7a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30d7a-113">See Also</span></span>  
 [<span data-ttu-id="30d7a-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="30d7a-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="30d7a-115">字串</span><span class="sxs-lookup"><span data-stu-id="30d7a-115">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="30d7a-116">.NET Framework 規則運算式</span><span class="sxs-lookup"><span data-stu-id="30d7a-116">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)

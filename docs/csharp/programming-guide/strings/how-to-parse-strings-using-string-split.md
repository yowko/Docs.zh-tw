---
title: "如何：使用 String.Split 剖析字串 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: d74c1d0760d4e776c2cf4c7dea1dac060c85a83c
ms.openlocfilehash: e25dbf6b86c82808622377c0618cd956541c6e09
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="ac850-102">如何：使用 String.Split 剖析字串 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="ac850-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="ac850-103">下列程式碼範例示範如何使用 <xref:System.String.Split%2A?displayProperty=fullName> 方法剖析字串。</span><span class="sxs-lookup"><span data-stu-id="ac850-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="ac850-104">當輸入時， <xref:System.String.Split%2A> 會採用字元陣列以表示用來分隔目標字串之有趣子字串的字元。</span><span class="sxs-lookup"><span data-stu-id="ac850-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="ac850-105">該函式會傳回子字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="ac850-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="ac850-106">這個範例會使用空格、逗號、句號、冒號和定位點，全部以包含這些分隔符號的陣列傳遞至 <xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="ac850-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="ac850-107">目標字串句子中的每個文字都會使用字串結果陣列來個別顯示。</span><span class="sxs-lookup"><span data-stu-id="ac850-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac850-108">範例</span><span class="sxs-lookup"><span data-stu-id="ac850-108">Example</span></span>  
 <span data-ttu-id="ac850-109">[!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac850-109">[!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac850-110">範例</span><span class="sxs-lookup"><span data-stu-id="ac850-110">Example</span></span>  
 <span data-ttu-id="ac850-111">根據預設，當目標字串中連續出現兩個分隔字元時，String.Split 會傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="ac850-111">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="ac850-112">您可以傳遞選擇性 StringSplitOptions.RemoveEmptyEntries 參數，以排除輸出中的任何空字串。</span><span class="sxs-lookup"><span data-stu-id="ac850-112">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="ac850-113">String.Split 可採用字串陣列 (做為分隔符號以剖析目標字串的字元序列，而不是單一字元)。</span><span class="sxs-lookup"><span data-stu-id="ac850-113">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac850-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac850-114">See Also</span></span>  
 <span data-ttu-id="ac850-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac850-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ac850-116">[字串](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac850-116">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 [<span data-ttu-id="ac850-117">.NET Framework 規則運算式</span><span class="sxs-lookup"><span data-stu-id="ac850-117">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)


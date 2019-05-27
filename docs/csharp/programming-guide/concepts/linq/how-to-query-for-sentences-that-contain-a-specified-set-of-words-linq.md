---
title: 作法：查詢包含指定字組的句子 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: 11f065594ed6b6c162ac95e0a1e6c502c1ad8de5
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584285"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a><span data-ttu-id="6a9e5-102">作法：查詢包含指定字組的句子 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6a9e5-102">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>
<span data-ttu-id="6a9e5-103">此範例示範如何在文字檔中尋找含有每個指定字組之相符項目的句子。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-103">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="6a9e5-104">雖然此範例硬式編碼了搜尋字詞的陣列，但也可以在執行階段將它動態填入。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-104">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="6a9e5-105">在此範例中，查詢會傳回包含 "Historically"、"data" 和 "integrated" 等字的句子。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-105">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a9e5-106">範例</span><span class="sxs-lookup"><span data-stu-id="6a9e5-106">Example</span></span>  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.   
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 <span data-ttu-id="6a9e5-107">查詢的運作方式是先將文字分割成句子，然後將句子分割成包含每個字的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-107">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="6a9e5-108">對於每個陣列，<xref:System.Linq.Enumerable.Distinct%2A> 方法會移除所有重複的字組，接著查詢會對字組陣列和 `wordsToMatch` 陣列執行 <xref:System.Linq.Enumerable.Intersect%2A> 作業。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-108">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="6a9e5-109">如果交集的計數與 `wordsToMatch` 陣列的計數相同，則所有字都可以在字組中找到，因而傳回原始句子。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-109">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>  
  
 <span data-ttu-id="6a9e5-110">在 <xref:System.String.Split%2A> 呼叫中，標點符號會當成分隔符號，以便從字串中移除。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-110">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="6a9e5-111">如果您不這麼做，則您的字串 "Historically," 與 `wordsToMatch` 陣列中的 "Historically" 不符。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-111">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="6a9e5-112">根據來源文字中找到的標點符號類型，您可能必須使用其他分隔符號。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-112">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6a9e5-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="6a9e5-113">Compiling the Code</span></span>  
<span data-ttu-id="6a9e5-114">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="6a9e5-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a9e5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a9e5-115">See also</span></span>

- [<span data-ttu-id="6a9e5-116">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="6a9e5-116">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)

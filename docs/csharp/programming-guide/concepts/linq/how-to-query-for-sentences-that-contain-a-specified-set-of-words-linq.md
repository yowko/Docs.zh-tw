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
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>作法：查詢包含指定字組的句子 (LINQ) (C#)
此範例示範如何在文字檔中尋找含有每個指定字組之相符項目的句子。 雖然此範例硬式編碼了搜尋字詞的陣列，但也可以在執行階段將它動態填入。 在此範例中，查詢會傳回包含 "Historically"、"data" 和 "integrated" 等字的句子。  
  
## <a name="example"></a>範例  
  
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
  
 查詢的運作方式是先將文字分割成句子，然後將句子分割成包含每個字的字串陣列。 對於每個陣列，<xref:System.Linq.Enumerable.Distinct%2A> 方法會移除所有重複的字組，接著查詢會對字組陣列和 `wordsToMatch` 陣列執行 <xref:System.Linq.Enumerable.Intersect%2A> 作業。 如果交集的計數與 `wordsToMatch` 陣列的計數相同，則所有字都可以在字組中找到，因而傳回原始句子。  
  
 在 <xref:System.String.Split%2A> 呼叫中，標點符號會當成分隔符號，以便從字串中移除。 如果您不這麼做，則您的字串 "Historically," 與 `wordsToMatch` 陣列中的 "Historically" 不符。 根據來源文字中找到的標點符號類型，您可能必須使用其他分隔符號。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。

## <a name="see-also"></a>另請參閱

- [LINQ 和字串 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)

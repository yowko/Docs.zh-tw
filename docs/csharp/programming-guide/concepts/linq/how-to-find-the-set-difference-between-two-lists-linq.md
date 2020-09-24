---
title: '如何尋找兩個清單之間的集合差異 (LINQ)  (c # ) '
description: '瞭解如何使用 c # 中的 LINQ 來比較兩個字串清單，並輸出位於一個清單但不在另一個清單中的行。'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 01aba16b3489e4bf21a76bc715b6d4d2c9d250dd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159055"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="ac3b7-103">如何尋找兩個清單之間的集合差異 (LINQ)  (c # ) </span><span class="sxs-lookup"><span data-stu-id="ac3b7-103">How to find the set difference between two lists (LINQ) (C#)</span></span>

<span data-ttu-id="ac3b7-104">此範例示範如何使用 LINQ 比較兩份字串清單，然後輸出在 names1.txt 但不在 names2.txt 中的字串行。</span><span class="sxs-lookup"><span data-stu-id="ac3b7-104">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="ac3b7-105">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="ac3b7-105">To create the data files</span></span>  
  
1. <span data-ttu-id="ac3b7-106">將 names1.txt 和 names2.txt 複製到您的方案資料夾，如 [如何合併和比較字串集合 (LINQ)  (c # ) ](./how-to-combine-and-compare-string-collections-linq.md)所示。</span><span class="sxs-lookup"><span data-stu-id="ac3b7-106">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac3b7-107">範例</span><span class="sxs-lookup"><span data-stu-id="ac3b7-107">Example</span></span>  
  
```csharp  
class CompareLists  
{
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <span data-ttu-id="ac3b7-108">C# 中某些查詢作業類型，如 <xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Union%2A> 和 <xref:System.Linq.Enumerable.Concat%2A>，只能使用以方法為基礎的語法表示。</span><span class="sxs-lookup"><span data-stu-id="ac3b7-108">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ac3b7-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ac3b7-109">Compiling the Code</span></span>  

 <span data-ttu-id="ac3b7-110">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ac3b7-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac3b7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac3b7-111">See also</span></span>

- [<span data-ttu-id="ac3b7-112">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="ac3b7-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)

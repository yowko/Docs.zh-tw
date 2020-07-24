---
title: '如何尋找兩個清單之間的集合差異（LINQ）（c #）'
description: '瞭解如何在 c # 中使用 LINQ 來比較兩個字串清單，並輸出其中一個清單中但不在另一個清單中的行。'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 24509488d91f9861ee9bf84277238bea7031e5f6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105082"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="23383-103">如何尋找兩個清單之間的集合差異（LINQ）（c #）</span><span class="sxs-lookup"><span data-stu-id="23383-103">How to find the set difference between two lists (LINQ) (C#)</span></span>
<span data-ttu-id="23383-104">此範例示範如何使用 LINQ 比較兩份字串清單，然後輸出在 names1.txt 但不在 names2.txt 中的字串行。</span><span class="sxs-lookup"><span data-stu-id="23383-104">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="23383-105">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="23383-105">To create the data files</span></span>  
  
1. <span data-ttu-id="23383-106">將 names1.txt 和 names2.txt 複製到方案資料夾，如[如何合併和比較字串集合（LINQ）（c #）](./how-to-combine-and-compare-string-collections-linq.md)中所示。</span><span class="sxs-lookup"><span data-stu-id="23383-106">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23383-107">範例</span><span class="sxs-lookup"><span data-stu-id="23383-107">Example</span></span>  
  
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
  
 <span data-ttu-id="23383-108">C# 中某些查詢作業類型，如 <xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Union%2A> 和 <xref:System.Linq.Enumerable.Concat%2A>，只能使用以方法為基礎的語法表示。</span><span class="sxs-lookup"><span data-stu-id="23383-108">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23383-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="23383-109">Compiling the Code</span></span>  
 <span data-ttu-id="23383-110">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="23383-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23383-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="23383-111">See also</span></span>

- [<span data-ttu-id="23383-112">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="23383-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)

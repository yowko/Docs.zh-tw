---
title: 作法：尋找兩個清單之間的集合差異 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: c8f01cb53665d01d4c7861bab758ecc9e0dcc3c8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585716"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="0de7e-102">作法：尋找兩個清單之間的集合差異 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0de7e-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="0de7e-103">此範例示範如何使用 LINQ 比較兩份字串清單，然後輸出在 names1.txt 但不在 names2.txt 中的字串行。</span><span class="sxs-lookup"><span data-stu-id="0de7e-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="0de7e-104">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="0de7e-104">To create the data files</span></span>  
  
1. <span data-ttu-id="0de7e-105">將 names1.txt 和 names2.txt 複製到您的方案資料夾，如[如何：合併和比較字串集合 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) 中所示。</span><span class="sxs-lookup"><span data-stu-id="0de7e-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0de7e-106">範例</span><span class="sxs-lookup"><span data-stu-id="0de7e-106">Example</span></span>  
  
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
  
 <span data-ttu-id="0de7e-107">C# 中某些查詢作業類型，如 <xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Union%2A> 和 <xref:System.Linq.Enumerable.Concat%2A>，只能使用以方法為基礎的語法表示。</span><span class="sxs-lookup"><span data-stu-id="0de7e-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0de7e-108">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0de7e-108">Compiling the Code</span></span>  
 <span data-ttu-id="0de7e-109">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="0de7e-109">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de7e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0de7e-110">See also</span></span>

- [<span data-ttu-id="0de7e-111">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="0de7e-111">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)

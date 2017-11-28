---
title: "如何：合併和比較字串集合 (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 25926e5b-fde2-4dc1-86a0-16ead7aa13d2
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c84e472b9b836fd996170543479e24a406ec2e8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-and-compare-string-collections-linq-c"></a><span data-ttu-id="bb596-102">如何：合併和比較字串集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bb596-102">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>
<span data-ttu-id="bb596-103">本例示範如何合併包含文字行的檔案，然後排序結果。</span><span class="sxs-lookup"><span data-stu-id="bb596-103">This example shows how to merge files that contain lines of text and then sort the results.</span></span> <span data-ttu-id="bb596-104">具體來說，它會示範如何在兩組文字行上執行簡單的串連、等位和交集。</span><span class="sxs-lookup"><span data-stu-id="bb596-104">Specifically, it shows how to perform a simple concatenation, a union, and an intersection on the two sets of text lines.</span></span>  
  
### <a name="to-set-up-the-project-and-the-text-files"></a><span data-ttu-id="bb596-105">設定專案和文字檔案</span><span class="sxs-lookup"><span data-stu-id="bb596-105">To set up the project and the text files</span></span>  
  
1.  <span data-ttu-id="bb596-106">將下列名稱複製到名為 names1.txt 的文字檔，並將它儲至專案資料夾：</span><span class="sxs-lookup"><span data-stu-id="bb596-106">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>  
  
    ```  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Beebe, Ann  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
    ```  
  
2.  <span data-ttu-id="bb596-107">將下列名稱複製到名為 names2.txt 的文字檔，並將它儲至專案資料夾。</span><span class="sxs-lookup"><span data-stu-id="bb596-107">Copy these names into a text file that is named names2.txt and save it in your project folder.</span></span> <span data-ttu-id="bb596-108">請注意兩個檔案有部分名稱相同。</span><span class="sxs-lookup"><span data-stu-id="bb596-108">Note that the two files have some names in common.</span></span>  
  
    ```  
    Liu, Jinghao  
    Bankov, Peter  
    Holm, Michael  
    Garcia, Hugo  
    Beebe, Ann  
    Gilchrist, Beth  
    Myrcha, Jacek  
    Giakoumakis, Leo  
    McLin, Nkenge  
    El Yassir, Mehdi  
    ```  
  
## <a name="example"></a><span data-ttu-id="bb596-109">範例</span><span class="sxs-lookup"><span data-stu-id="bb596-109">Example</span></span>  
  
```csharp  
class MergeStrings  
    {  
        static void Main(string[] args)  
        {  
            //Put text files in your solution folder  
            string[] fileA = System.IO.File.ReadAllLines(@"../../../names1.txt");  
            string[] fileB = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
            //Simple concatenation and sort. Duplicates are preserved.  
            IEnumerable<string> concatQuery =  
                fileA.Concat(fileB).OrderBy(s => s);  
  
            // Pass the query variable to another function for execution.  
            OutputQueryResults(concatQuery, "Simple concatenate and sort. Duplicates are preserved:");  
  
            // Concatenate and remove duplicate names based on  
            // default string comparer.  
            IEnumerable<string> uniqueNamesQuery =  
                fileA.Union(fileB).OrderBy(s => s);  
            OutputQueryResults(uniqueNamesQuery, "Union removes duplicate names:");  
  
            // Find the names that occur in both files (based on  
            // default string comparer).  
            IEnumerable<string> commonNamesQuery =  
                fileA.Intersect(fileB);  
            OutputQueryResults(commonNamesQuery, "Merge based on intersect:");  
  
            // Find the matching fields in each list. Merge the two   
            // results by using Concat, and then  
            // sort using the default string comparer.  
            string nameMatch = "Garcia";  
  
            IEnumerable<String> tempQuery1 =  
                from name in fileA  
                let n = name.Split(',')  
                where n[0] == nameMatch  
                select name;  
  
            IEnumerable<string> tempQuery2 =  
                from name2 in fileB  
                let n2 = name2.Split(',')  
                where n2[0] == nameMatch  
                select name2;  
  
            IEnumerable<string> nameMatchQuery =  
                tempQuery1.Concat(tempQuery2).OrderBy(s => s);  
            OutputQueryResults(nameMatchQuery, String.Format("Concat based on partial name match \"{0}\":", nameMatch));  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
  
        static void OutputQueryResults(IEnumerable<string> query, string message)  
        {  
            Console.WriteLine(System.Environment.NewLine + message);  
            foreach (string item in query)  
            {  
                Console.WriteLine(item);  
            }  
            Console.WriteLine("{0} total names in list", query.Count());  
        }  
    }  
    /* Output:  
        Simple concatenate and sort. Duplicates are preserved:  
        Aw, Kam Foo  
        Bankov, Peter  
        Bankov, Peter  
        Beebe, Ann  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        20 total names in list  
  
        Union removes duplicate names:  
        Aw, Kam Foo  
        Bankov, Peter  
        Beebe, Ann  
        El Yassir, Mehdi  
        Garcia, Debra  
        Garcia, Hugo  
        Giakoumakis, Leo  
        Gilchrist, Beth  
        Guy, Wey Yuan  
        Holm, Michael  
        Liu, Jinghao  
        McLin, Nkenge  
        Myrcha, Jacek  
        Noriega, Fabricio  
        Potra, Cristina  
        Toyoshima, Tim  
        16 total names in list  
  
        Merge based on intersect:  
        Bankov, Peter  
        Holm, Michael  
        Garcia, Hugo  
        Beebe, Ann  
        4 total names in list  
  
        Concat based on partial name match "Garcia":  
        Garcia, Debra  
        Garcia, Hugo  
        Garcia, Hugo  
        3 total names in list  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb596-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bb596-110">Compiling the Code</span></span>  
 <span data-ttu-id="bb596-111">建立以 .NET Framework 3.5 版或更新版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="bb596-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb596-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb596-112">See Also</span></span>  
 [<span data-ttu-id="bb596-113">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="bb596-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="bb596-114">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="bb596-114">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)

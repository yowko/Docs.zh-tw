---
title: '如何依任何字或欄位排序或篩選文字資料（LINQ）（c #）'
description: 瞭解如何依任何字或欄位排序或篩選文字資料。 請參閱依行中的任何欄位排序結構化文字的範例。
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: f27ce44f4b0b05bc9094b7e108af8f65170bb58a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301316"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="bb236-104">如何依任何字或欄位排序或篩選文字資料（LINQ）（c #）</span><span class="sxs-lookup"><span data-stu-id="bb236-104">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>
<span data-ttu-id="bb236-105">下列範例示範如何依行中的任一欄位，來排序多行結構化文字 (例如逗號分隔值)。</span><span class="sxs-lookup"><span data-stu-id="bb236-105">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="bb236-106">此欄位可能會在執行階段以動態方式指定。</span><span class="sxs-lookup"><span data-stu-id="bb236-106">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="bb236-107">假設 scores.csv 中的欄位各代表學生的學號和四個測驗分數。</span><span class="sxs-lookup"><span data-stu-id="bb236-107">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="bb236-108">建立內含資料的檔案</span><span class="sxs-lookup"><span data-stu-id="bb236-108">To create a file that contains data</span></span>  
  
1. <span data-ttu-id="bb236-109">複製[如何從不同的檔案聯結內容（LINQ）（c #）](./how-to-join-content-from-dissimilar-files-linq.md)主題中的 scores.csv 資料，並將它儲存至您的方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="bb236-109">Copy the scores.csv data from the topic [How to join content from dissimilar files (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb236-110">範例</span><span class="sxs-lookup"><span data-stu-id="bb236-110">Example</span></span>  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 <span data-ttu-id="bb236-111">此範例也會示範如何從方法傳回查詢變數。</span><span class="sxs-lookup"><span data-stu-id="bb236-111">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb236-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bb236-112">Compiling the Code</span></span>  

<span data-ttu-id="bb236-113">建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。</span><span class="sxs-lookup"><span data-stu-id="bb236-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bb236-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb236-114">See also</span></span>

- [<span data-ttu-id="bb236-115">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="bb236-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)

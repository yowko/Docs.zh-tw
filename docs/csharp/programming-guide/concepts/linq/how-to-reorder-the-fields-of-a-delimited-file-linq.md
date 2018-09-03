---
title: 如何：重新排列有分隔符號的檔案中的欄位 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 4c7dcbea938711904d42228d9c3bd24abffa4f35
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43384538"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a><span data-ttu-id="27418-102">如何：重新排列有分隔符號的檔案中的欄位 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="27418-102">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>
<span data-ttu-id="27418-103">逗號分隔值 (CSV) 檔案是一種文字檔，常用來儲存試算表資料或其他以資料列和資料行呈現的表格式資料。</span><span class="sxs-lookup"><span data-stu-id="27418-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="27418-104">使用 <xref:System.String.Split%2A> 方法隔開欄位後，就可以利用 LINQ 輕鬆地查詢和管理 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="27418-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="27418-105">事實上，您可以使用此相同的方法來重新排列任何結構化文字行中的其中幾部分，而不限於 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="27418-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="27418-106">在下列範例中，假設有三個資料行分別表示學生的「姓氏」、「名字」和「學號」。</span><span class="sxs-lookup"><span data-stu-id="27418-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="27418-107">這些欄位會依照學生的姓氏字母排序。</span><span class="sxs-lookup"><span data-stu-id="27418-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="27418-108">此查詢會產生新的順序，其中會先出現學號資料行，後面接著結合學生姓氏和名字的第二個資料行。</span><span class="sxs-lookup"><span data-stu-id="27418-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="27418-109">這些行會根據學號欄位重新排列。</span><span class="sxs-lookup"><span data-stu-id="27418-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="27418-110">結果會儲存至新的檔案，而且不會修改原始資料。</span><span class="sxs-lookup"><span data-stu-id="27418-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="27418-111">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="27418-111">To create the data file</span></span>  
  
1.  <span data-ttu-id="27418-112">將下列幾行複製到名為 spreadsheet1.csv 的純文字檔。</span><span class="sxs-lookup"><span data-stu-id="27418-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="27418-113">將此檔案儲存在您的專案資料夾中。</span><span class="sxs-lookup"><span data-stu-id="27418-113">Save the file in your project folder.</span></span>  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a><span data-ttu-id="27418-114">範例</span><span class="sxs-lookup"><span data-stu-id="27418-114">Example</span></span>  
  
```csharp  
class CSVFiles  
{  
    static void Main(string[] args)  
    {  
        // Create the IEnumerable data source  
        string[] lines = System.IO.File.ReadAllLines(@"../../../spreadsheet1.csv");  
  
        // Create the query. Put field 2 first, then  
        // reverse and combine fields 0 and 1 from the old field  
        IEnumerable<string> query =  
            from line in lines  
            let x = line.Split(',')  
            orderby x[2]  
            select x[2] + ", " + (x[1] + " " + x[0]);  
  
        // Execute the query and write out the new file. Note that WriteAllLines  
        // takes a string[], so ToArray is called on the query.  
        System.IO.File.WriteAllLines(@"../../../spreadsheet2.csv", query.ToArray());  
  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output to spreadsheet2.csv:  
111, Svetlana Omelchenko  
112, Claire O'Donnell  
113, Sven Mortensen  
114, Cesar Garcia  
115, Debra Garcia  
116, Fadi Fakhouri  
117, Hanying Feng  
118, Hugo Garcia  
119, Lance Tucker  
120, Terry Adams  
121, Eugene Zabokritski  
122, Michael Tucker  
 */  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27418-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="27418-115">Compiling the Code</span></span>  
 <span data-ttu-id="27418-116">建立以 .NET Framework 3.5 版或更新版本為目標的專案，該專案包含 System.Core.dll 的參考，以及 System.Linq 和 System.IO 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="27418-116">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27418-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="27418-117">See Also</span></span>  
 [<span data-ttu-id="27418-118">LINQ 和字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="27418-118">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="27418-119">LINQ 和檔案目錄 (C#)</span><span class="sxs-lookup"><span data-stu-id="27418-119">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [<span data-ttu-id="27418-120">如何：從 CSV 檔案產生 XML</span><span class="sxs-lookup"><span data-stu-id="27418-120">How to: Generate XML from CSV Files</span></span>](https://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)

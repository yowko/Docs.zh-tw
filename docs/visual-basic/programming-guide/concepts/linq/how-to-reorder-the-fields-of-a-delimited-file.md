---
title: "如何︰ 重新排列分隔檔案 (LINQ) (Visual Basic) 的欄位 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8540dff06e146a1846063e11e3382e9457f9e412
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="bd6a9-102">如何︰ 重新排列分隔檔案 (LINQ) (Visual Basic) 的欄位</span><span class="sxs-lookup"><span data-stu-id="bd6a9-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="bd6a9-103">以逗號分隔值 (CSV) 檔案是文字檔經常用來儲存試算表資料或其他由資料列和資料行的表格式資料。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="bd6a9-104">使用<xref:System.String.Split%2A>方法來分隔的欄位，它可以非常輕易地查詢及操作使用 LINQ 的 CSV 檔案。</xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="bd6a9-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="bd6a9-105">事實上，相同的技巧可以用來重新排列任何結構化一行文字; 組件這並不限於 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="bd6a9-106">在下列範例中，假設三個資料行代表學生 「 姓氏 」 「 first name 」 和 「 識別碼 」。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="bd6a9-107">欄位是根據學生的姓氏的字母順序。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="bd6a9-108">此查詢會產生新的順序中的識別碼資料行顯示第一，後面接著結合學生的名字和姓氏的第二個資料行。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="bd6a9-109">這些行會根據 ID 欄位。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="bd6a9-110">結果會儲存到新檔案並不會修改原始資料。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="bd6a9-111">建立資料檔</span><span class="sxs-lookup"><span data-stu-id="bd6a9-111">To create the data file</span></span>  
  
1.  <span data-ttu-id="bd6a9-112">將下列幾行複製到名為 spreadsheet1.csv 純文字檔。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="bd6a9-113">在您的專案資料夾中儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="bd6a9-113">Save the file in your project folder.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bd6a9-114">範例</span><span class="sxs-lookup"><span data-stu-id="bd6a9-114">Example</span></span>  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd6a9-115">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="bd6a9-115">Compiling the Code</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6a9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd6a9-116">See Also</span></span>  
 <span data-ttu-id="bd6a9-117">[LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="bd6a9-117">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="bd6a9-118"> [LINQ 和檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md) </span><span class="sxs-lookup"><span data-stu-id="bd6a9-118"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md) </span></span>  
<span data-ttu-id="bd6a9-119"> [如何：從 CSV 檔案產生 XML](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)</span><span class="sxs-lookup"><span data-stu-id="bd6a9-119"> [How to: Generate XML from CSV Files](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)</span></span>

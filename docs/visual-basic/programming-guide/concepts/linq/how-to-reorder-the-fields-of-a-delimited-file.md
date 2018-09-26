---
title: 如何： 重新排列欄位的分隔符號的檔案 (LINQ) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: f9322ac9601deffd110c962a9ed8b502a02092ee
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172663"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a>如何： 重新排列欄位的分隔符號的檔案 (LINQ) (Visual Basic)
逗號分隔值 (CSV) 檔案是一種文字檔，常用來儲存試算表資料或其他以資料列和資料行呈現的表格式資料。 使用 <xref:System.String.Split%2A> 方法隔開欄位後，就可以利用 LINQ 輕鬆地查詢和管理 CSV 檔案。 事實上，您可以使用此相同的方法來重新排列任何結構化文字行中的其中幾部分，而不限於 CSV 檔案。  
  
 在下列範例中，假設有三個資料行分別表示學生的「姓氏」、「名字」和「學號」。 這些欄位會依照學生的姓氏字母排序。 此查詢會產生新的順序，其中會先出現學號資料行，後面接著結合學生姓氏和名字的第二個資料行。 這些行會根據學號欄位重新排列。 結果會儲存至新的檔案，而且不會修改原始資料。  
  
### <a name="to-create-the-data-file"></a>建立資料檔  
  
1.  將下列幾行複製到名為 spreadsheet1.csv 的純文字檔。 將此檔案儲存在您的專案資料夾中。  
  
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
  
## <a name="example"></a>範例  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
## <a name="see-also"></a>另請參閱

- [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
- [LINQ 與檔案目錄 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [如何：從 CSV 檔案產生 XML](../../../../visual-basic/programming-guide/concepts/linq/how-to-generate-xml-from-csv-files.md)

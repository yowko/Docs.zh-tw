---
title: 作法：重新排列分隔檔的欄位 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 4e62d82c-61b7-4f18-b9a1-86723746d7d2
ms.openlocfilehash: 1507d0f743070f15b8e64d5dcfb1b9499470b123
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592696"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-c"></a>作法：重新排列分隔檔的欄位 (LINQ) (C#)
逗號分隔值 (CSV) 檔案是一種文字檔，常用來儲存試算表資料或其他以資料列和資料行呈現的表格式資料。 使用 <xref:System.String.Split%2A> 方法隔開欄位後，就可以利用 LINQ 輕鬆地查詢和管理 CSV 檔案。 事實上，您可以使用此相同的方法來重新排列任何結構化文字行中的其中幾部分，而不限於 CSV 檔案。  
  
 在下列範例中，假設有三個資料行分別表示學生的「姓氏」、「名字」和「學號」。 這些欄位會依照學生的姓氏字母排序。 此查詢會產生新的順序，其中會先出現學號資料行，後面接著結合學生姓氏和名字的第二個資料行。 這些行會根據學號欄位重新排列。 結果會儲存至新的檔案，而且不會修改原始資料。  
  
### <a name="to-create-the-data-file"></a>建立資料檔  
  
1. 將下列幾行複製到名為 spreadsheet1.csv 的純文字檔。 將此檔案儲存在您的專案資料夾中。  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
建立 C# 主控台應用程式專案，以及具有 `using` 指示詞的 System.Linq 和 System.IO 命名空間。
  
## <a name="see-also"></a>另請參閱

- [LINQ 和字串 (C#)](./linq-and-strings.md)
- [LINQ 和檔案目錄 (C#)](./linq-and-file-directories.md)
- [如何：從 CSV 檔案產生 XML (C#)](./how-to-generate-xml-from-csv-files.md)

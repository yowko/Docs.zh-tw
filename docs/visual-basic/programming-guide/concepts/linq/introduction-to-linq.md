---
title: LINQ (Visual Basic) 簡介
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 371801e1730c578b039adb6a88bd0bcdfd186db7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644858"
---
# <a name="introduction-to-linq-visual-basic"></a>LINQ (Visual Basic) 簡介
Language-Integrated Query (LINQ) 是 .NET Framework 3.5 版中引進的創新技術，用來填補許多物件與資料之間的缺口。  
  
 傳統上，資料查詢是以簡單的字串表示，既不會在編譯時進行類型檢查，也不支援 IntelliSense。 此外，您必須針對每個資料來源型別 (例如 SQL 資料庫、XML 文件、各種 Web 服務等等) 學習不同的查詢語言。 LINQ 可讓*查詢*在 Visual Basic 中的第一級語言建構。 您可以使用語言關鍵字和熟悉的運算子，針對強型別的物件集合撰寫查詢。  
  
 您可以在 Visual Basic 中撰寫 LINQ 查詢 SQL Server 資料庫、 XML 文件、 ADO.NET 資料集和任何支援的物件集合<xref:System.Collections.IEnumerable>或泛型<xref:System.Collections.Generic.IEnumerable%601>介面。 也有協力廠商針對許多 Web 服務和其他資料庫實作提供 LINQ 支援。  
  
 您可以在新的專案中使用 LINQ 查詢，也可以與現有專案中的非 LINQ 查詢一起使用。 唯一的必要條件是專案要以 .NET Framework 3.5 或更新版本為目標。  
  
 下圖顯示 Visual Studio 中針對 SQL Server 資料庫以 C# 和 Visual Basic 撰寫之部分完成的 LINQ 查詢，其中有完整的類型檢查和 IntelliSense 支援。  
  
 ![具有 Intellisense 的 LINQ 查詢](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>後續步驟  
 若要深入了解更多詳細 LINQ，一開始熟悉的使用者入門的區段中的一些基本概念[在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)，然後讀取您所 LINQ 技術的文件想要：  
  
-   SQL Server 資料庫：[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
-   XML 文件： [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET 資料集：[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   .NET 集合、 檔案、 字串等： [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>另請參閱  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)

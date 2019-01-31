---
title: LINQ 簡介 (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: c74c4d3261354bdd2b8194371b4b37f014397e85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626559"
---
# <a name="introduction-to-linq-c"></a>LINQ 簡介 (C#)
Language-Integrated Query (LINQ) 是 .NET Framework 3.5 版中引進的創新技術，用來填補許多物件與資料之間的缺口。  
  
 傳統上，針對資料的查詢是以簡單字串表示，而不會在編譯期間進行型別檢查，或提供 IntelliSense 支援。 此外，您還必須了解每種資料來源類型的不同查詢語言：SQL 資料庫、XML 文件、各種 Web 服務等。 LINQ 會在 C# 中將「查詢」設為第一類語言建構。 您可以使用語言關鍵字和熟悉的運算子，針對強型別的物件集合撰寫查詢。  
  
 您可以使用 C# 針對下列項目撰寫 LINQ 查詢：SQL Server 資料庫、XML 文件、ADO.NET 資料集，以及支援 <xref:System.Collections.IEnumerable> 或泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面的任何物件集合。 也有協力廠商針對許多 Web 服務和其他資料庫實作提供 LINQ 支援。  
  
 您可以在新的專案中使用 LINQ 查詢，也可以與現有專案中的非 LINQ 查詢一起使用。 唯一的必要條件是專案要以 .NET Framework 3.5 或更新版本為目標。  
  
 下圖顯示 Visual Studio 中針對 SQL Server 資料庫以 C# 和 Visual Basic 撰寫之部分完成的 LINQ 查詢，其中有完整的類型檢查和 IntelliSense 支援。  
  
 ![具有 Intellisense 的 LINQ 查詢](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>後續步驟  
 若要深入了解 LINQ 的詳細資料，請先參閱[開始使用 C# 中的 LINQ](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) 的＜使用者入門＞一節以熟悉一些基本概念，然後閱讀您感興趣的 LINQ 技術文件：  
  
-   SQL Server 資料庫：[LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
-   XML 文件：[LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET 資料集：[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
-   .NET 集合、檔案、字串等：[LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)

---
title: LINQ 簡介
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 58613281d79769bfb5515f1291feb9b502a1e846
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549963"
---
# <a name="introduction-to-linq-visual-basic"></a>LINQ 簡介 (Visual Basic)
Language-Integrated Query (LINQ) 是 .NET Framework 3.5 版中引進的創新技術，用來填補許多物件與資料之間的缺口。  
  
 傳統上，資料查詢是以簡單的字串表示，既不會在編譯時進行類型檢查，也不支援 IntelliSense。 此外，您還必須針對每種資料來源類型學習不同的查詢語言：SQL 資料庫、XML 文件、各種 Web 服務等等。 LINQ 會讓 *查詢* 成為 Visual Basic 中的第一級語言結構。 您可以使用語言關鍵字和熟悉的運算子，針對強型別的物件集合撰寫查詢。  
  
 您可以在 Visual Basic 中撰寫 SQL Server 資料庫、XML 檔、ADO.NET 資料集，以及任何支援或泛型介面之物件集合的 LINQ 查詢 <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> 。 也有協力廠商針對許多 Web 服務和其他資料庫實作提供 LINQ 支援。  
  
 您可以在新的專案中使用 LINQ 查詢，也可以與現有專案中的非 LINQ 查詢一起使用。 唯一的必要條件是專案要以 .NET Framework 3.5 或更新版本為目標。  
  
 下圖顯示 Visual Studio 中針對 SQL Server 資料庫以 C# 和 Visual Basic 撰寫之部分完成的 LINQ 查詢，其中有完整的類型檢查和 IntelliSense 支援。  
  
 ![顯示具有 Intellisense 的 LINQ 查詢的圖表。](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a>後續步驟  
 若要深入瞭解 LINQ 的詳細資訊，請先熟悉消費者入門一節中的一些基本概念， [消費者入門在 Visual Basic 中使用 linq](getting-started-with-linq.md)，然後閱讀您感興趣的 linq 技術檔：  
  
- SQL Server 資料庫：[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
- XML 檔： [LINQ to XML (Visual Basic) ](../../../../standard/linq/linq-xml-overview.md)  
  
- ADO.NET 資料集：[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
- .NET 集合、檔案、字串等等： [LINQ to Objects (Visual Basic) ](linq-to-objects.md)  
  
## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) (Visual Basic)](index.md)

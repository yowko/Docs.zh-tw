---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 1c03cca80de6003a4e49278871983ed7fcb3dc0b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200662"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet

LINQ to DataSet 可讓您更輕鬆且更快速地查詢在物件中快取的資料 <xref:System.Data.DataSet> 。 具體來說，LINQ to DataSet 可讓開發人員從程式設計語言本身撰寫查詢，而不是使用不同的查詢語言，藉以簡化查詢。 這特別適用于 Visual Studio 開發人員，他們現在可以利用查詢中 Visual Studio 所提供的編譯時期語法檢查、靜態類型和 IntelliSense 支援。  
  
 LINQ to DataSet 也可以用來查詢已從一或多個資料來源合併的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
 LINQ to DataSet 的功能主要是透過和類別中的擴充方法來公開 <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> 。 LINQ to DataSet 建基於並使用現有的 ADO.NET 架構，而不是用來取代應用程式程式碼中的 ADO.NET。 現有的 ADO.NET 程式碼將繼續在 LINQ to DataSet 應用程式中運作。 下圖將說明 LINQ to DataSet 與 ADO.NET 以及資料存放區的關聯性。  
  
 ![顯示 LINQ to DataSet 以 ADO.NET 提供者為基礎的圖表。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>本節內容  

 [快速入門](getting-started-linq-to-dataset.md)  
  
 [程式設計指南](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>參考  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ 和 ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)

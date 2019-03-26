---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: d7ebf32467c7ed1d54279a93c5052e7a52dc52f7
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462717"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓您更方便且更快速地查詢在 <xref:System.Data.DataSet> 物件中快取的資料。 具體來說，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]簡化查詢，讓開發人員撰寫查詢，從程式語言本身，而不是使用不同的查詢語言。 這是特別適用於 Visual Studio 開發人員來說，現在可以利用的編譯時間語法檢查、 靜態型別和 Visual Studio，在查詢中所提供的 IntelliSense 支援。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也可用來查詢已經從一個或多個資料來源合併的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]功能會公開主要是透過的擴充方法<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 建置基礎，並使用現有[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]架構，而不是取代[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]應用程式程式碼中。 現有的 ADO.NET 2.0 程式碼將繼續在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 應用程式中運作。 下圖將說明 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 與 [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] 的關聯性以及資料存放區。  
  
 ![此圖表顯示 LINQ to DataSet 以 ADO.NET 提供者為基礎。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>參考資料  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>另請參閱
- [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ 和 ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)

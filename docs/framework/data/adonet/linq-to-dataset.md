---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504362"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ to DataSet 可輕鬆並更快速地對資料的查詢快取在<xref:System.Data.DataSet>物件。 具體而言，LINQ to DataSet 可簡化讓開發人員撰寫查詢，從程式語言本身，而不是使用不同的查詢語言查詢。 這是特別適用於 Visual Studio 開發人員來說，現在可以利用的編譯時間語法檢查、 靜態型別和 Visual Studio，在查詢中所提供的 IntelliSense 支援。  
  
 也可以用 LINQ to DataSet 查詢已合併一或多個資料來源的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
 LINQ to DataSet 功能會公開主要是透過的擴充方法<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別。 LINQ to DataSet 是根據和使用現有的 ADO.NET 架構，而不是取代應用程式程式碼中的 ADO.NET。 現有的 ADO.NET 程式碼會繼續在 LINQ to DataSet 應用程式中運作。 LINQ to ADO.NET 和資料存放區的資料集的關聯性是由下列圖所示。  
  
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

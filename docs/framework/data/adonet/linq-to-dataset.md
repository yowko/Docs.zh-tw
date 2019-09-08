---
title: LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783782"
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
LINQ to DataSet 可讓您更輕鬆且更快速地查詢在<xref:System.Data.DataSet>物件中快取的資料。 具體而言，LINQ to DataSet 可讓開發人員從程式設計語言本身撰寫查詢，而不是使用不同的查詢語言，藉此簡化查詢。 這對於 Visual Studio 開發人員特別有用，他們現在可以利用查詢中 Visual Studio 所提供的編譯時間語法檢查、靜態型別和 IntelliSense 支援。  
  
 LINQ to DataSet 也可以用來查詢已從一個或多個資料來源合併的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
 LINQ to DataSet 功能主要是透過<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別中的擴充方法公開。 LINQ to DataSet 是以現有的 ADO.NET 架構為基礎，而不是用來取代應用程式程式碼中的 ADO.NET。 現有的 ADO.NET 程式碼會繼續在 LINQ to DataSet 應用程式中運作。 下圖說明 LINQ to DataSet ADO.NET 與資料存放區的關聯性。  
  
 ![此圖顯示 LINQ to DataSet 是以 ADO.NET 提供者為基礎。](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>本節內容  
 [快速入門](getting-started-linq-to-dataset.md)  
  
 [程式設計手冊](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>參考資料  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>另請參閱

- [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ 和 ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)

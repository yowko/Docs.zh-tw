---
title: LINQ to DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de0f11149c2ec587372b9e25f39f35f8552503c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-dataset"></a>LINQ to DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 可讓您更方便且更快速地查詢在 <xref:System.Data.DataSet> 物件中快取的資料。 具體來說，[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]簡化查詢，讓開發人員從程式語言本身撰寫查詢而不是使用不同的查詢語言。 這是特別適用於[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]開發人員現在能夠利用編譯時期語法檢查、 靜態型別和 IntelliSense 支援所提供的優點[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]在查詢中。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也可用來查詢已經從一個或多個資料來源合併的資料。 這點可以實現許多資料表示和處理方式需要彈性的案例，例如本機查詢彙總的資料和在 Web 應用程式中進行中介層 (Middle Tier) 快取。 尤其，一般報表、分析和商務智慧應用程式都需要這種管理方法。  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]功能中的擴充方法主要是透過公開<xref:System.Data.DataRowExtensions>和<xref:System.Data.DataTableExtensions>類別。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]為基礎，並使用現有[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]架構，而不是取代[!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)]應用程式程式碼中。 現有的 ADO.NET 2.0 程式碼將繼續在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 應用程式中運作。 下圖將說明 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 與 [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] 的關聯性以及資料存放區。  
  
 ![LINQ to DataSet 根據 ADO.NET 提供者](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>本章節內容  
 [快速入門](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>參考資料  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>另請參閱  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ 和 ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)

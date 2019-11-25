---
title: WCF 資料服務用戶端程式庫
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: e078ba07072f71332aa2f19681b142df946ec391
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975066"
---
# <a name="wcf-data-services-client-library"></a>WCF 資料服務用戶端程式庫
如果任何應用程式可以傳送 HTTP 要求並處理資料服務傳回的 OData 摘要，就可以與以開放式資料通訊協定（OData）為基礎的資料服務互動。 此互通性可讓您從各種 Web 啟用的應用程式存取 OData 服務。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含用戶端程式庫，可在您從 .NET Framework 或 Silverlight 應用程式取用 OData 摘要時，提供更豐富的程式設計體驗。  
  
 用戶端程式庫的兩個主要類別是 <xref:System.Data.Services.Client.DataServiceContext> 類別和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別。 <xref:System.Data.Services.Client.DataServiceContext> 類別會封裝針對特定資料服務支援的作業。 雖然 OData 服務是無狀態的，但內容並不是。 因此，您可以使用 <xref:System.Data.Services.Client.DataServiceContext> 類別來維護與資料服務互動之間的狀態，以便支援變更管理之類的功能。 這個類別也可以管理識別及追蹤變更。 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別表示針對特定實體集的查詢。  
  
 本節將描述如何使用用戶端程式庫，存取和變更 .NET Framework 用戶端應用程式的資料。 如需如何搭配 Silverlight 架構應用程式使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫的詳細資訊，請參閱[WCF Data Services （Silverlight）](https://go.microsoft.com/fwlink/?LinkId=186016)。 有其他用戶端程式庫可讓您在其他種類的應用程式中取用 OData 摘要。 如需詳細資訊，請參閱[ODATA SDK](https://go.microsoft.com/fwlink/?LinkID=185796)。  
  
## <a name="in-this-section"></a>本章節內容  
 [產生資料服務用戶端程式庫](generating-the-data-service-client-library-wcf-data-services.md)  
 描述如何產生以 OData 摘要為基礎的用戶端程式庫和用戶端資料服務類別。  
  
 [查詢資料服務](querying-the-data-service-wcf-data-services.md)  
 描述如何使用用戶端程式庫查詢 .NET Framework 架構應用程式的資料服務。  
  
 [載入延後內容](loading-deferred-content-wcf-data-services.md)  
 描述如何載入不包含在初始查詢回應中的額外內容。  
  
 [更新資料服務](updating-the-data-service-wcf-data-services.md)  
 描述如何使用用戶端程式庫建立、修改，以及刪除實體及關聯性。  
  
 [非同步作業](asynchronous-operations-wcf-data-services.md)  
 描述以非同步方式，搭配用戶端程式庫提供的機能與資料服務一起使用。  
  
 [批次處理作業](batching-operations-wcf-data-services.md)  
 描述如何使用用戶端程式庫，在單一批次中將多個要求傳送至資料服務。  
  
 [將資料繫結至控制項](binding-data-to-controls-wcf-data-services.md)  
 描述如何將控制項系結至資料服務所傳回的 OData 摘要。  
  
 [呼叫服務作業](calling-service-operations-wcf-data-services.md)  
 說明如何使用用戶端程式庫呼叫服務作業。  
  
 [管理資料服務內容](managing-the-data-service-context-wcf-data-services.md)  
 說明用於管理用戶端程式庫行為的選項。  
  
 [使用二進位資料](working-with-binary-data-wcf-data-services.md)  
 說明如何存取及變更資料服務當做資料流傳回的二進位資料。  
  
## <a name="see-also"></a>請參閱

- [定義 WCF Data Services](defining-wcf-data-services.md)
- [使用者入門](getting-started-with-wcf-data-services.md)

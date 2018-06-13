---
title: WCF 資料服務用戶端程式庫
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 95ca3ab8768b59b52640cfd17d230a544a8b2052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365510"
---
# <a name="wcf-data-services-client-library"></a>WCF 資料服務用戶端程式庫
任何可以傳送 HTTP 要求並處理資料服務傳回之 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要的應用程式，都可以與 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型資料服務互動。 這個互通性可讓您存取許多 Web 架構應用程式的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型服務。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含提供更豐富的程式設計體驗，當您使用的用戶端程式庫[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]從.NET Framework 或 Silverlight 架構應用程式摘要。  
  
 用戶端程式庫的兩個主要類別是 <xref:System.Data.Services.Client.DataServiceContext> 類別和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別。 <xref:System.Data.Services.Client.DataServiceContext> 類別會封裝針對特定資料服務支援的作業。 雖然 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務沒有狀態，但是內容具有狀態。 因此，您可以使用<xref:System.Data.Services.Client.DataServiceContext>類別上的用戶端以支援資料服務互動之間維護狀態的功能變更管理之類。 這個類別也可以管理識別及追蹤變更。 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別表示針對特定實體集的查詢。  
  
 本節將描述如何使用用戶端程式庫，存取和變更 .NET Framework 用戶端應用程式的資料。 如需有關如何使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫，與以 Silverlight 為基礎的應用程式，請參閱[WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016)。 其他用戶端程式庫，可讓您使用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]其他種類的應用程式中的摘要。 如需詳細資訊，請參閱[OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)。  
  
## <a name="in-this-section"></a>本節內容  
 [產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 描述如何產生用戶端程式庫和用戶端資料服務類別為基礎的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要。  
  
 [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 描述如何使用用戶端程式庫查詢 .NET Framework 架構應用程式的資料服務。  
  
 [載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 描述如何載入不包含在初始查詢回應中的額外內容。  
  
 [更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 描述如何使用用戶端程式庫建立、修改，以及刪除實體及關聯性。  
  
 [非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 描述以非同步方式，搭配用戶端程式庫提供的機能與資料服務一起使用。  
  
 [批次處理作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 描述如何使用用戶端程式庫，在單一批次中將多個要求傳送至資料服務。  
  
 [將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 描述如何將繫結控制項至[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]資料服務所傳回的摘要。  
  
 [呼叫服務作業](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 說明如何使用用戶端程式庫呼叫服務作業。  
  
 [管理資料服務內容](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 說明用於管理用戶端程式庫行為的選項。  
  
 [使用二進位資料](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 說明如何存取及變更資料服務當做資料流傳回的二進位資料。  
  
## <a name="see-also"></a>另請參閱  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

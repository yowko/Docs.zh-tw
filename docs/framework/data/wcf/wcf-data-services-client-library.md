---
title: WCF 資料服務用戶端程式庫
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 545442b0086361c8ce8c0482801afc10b1fee96e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779677"
---
# <a name="wcf-data-services-client-library"></a>WCF 資料服務用戶端程式庫
任何可以傳送 HTTP 要求並處理資料服務傳回之 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要的應用程式，都可以與 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型資料服務互動。 這個互通性可讓您存取許多 Web 架構應用程式的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型服務。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]包含用戶端程式庫，可在您[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]從 .NET Framework 或 Silverlight 架構應用程式取用摘要時，提供更豐富的程式設計體驗。  
  
 用戶端程式庫的兩個主要類別是 <xref:System.Data.Services.Client.DataServiceContext> 類別和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別。 <xref:System.Data.Services.Client.DataServiceContext> 類別會封裝針對特定資料服務支援的作業。 雖然 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務沒有狀態，但是內容具有狀態。 因此，您可以使用<xref:System.Data.Services.Client.DataServiceContext>類別來維護與資料服務互動之間的狀態，以便支援變更管理之類的功能。 這個類別也可以管理識別及追蹤變更。 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別表示針對特定實體集的查詢。  
  
 本節將描述如何使用用戶端程式庫，存取和變更 .NET Framework 用戶端應用程式的資料。 如需如何搭配 Silverlight 應用程式使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫的詳細資訊，請參閱[WCF Data Services （Silverlight）](https://go.microsoft.com/fwlink/?LinkId=186016)。 有其他用戶端程式庫可讓您[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]在其他種類的應用程式中取用摘要。 如需詳細資訊，請參閱[ODATA SDK](https://go.microsoft.com/fwlink/?LinkID=185796)。  
  
## <a name="in-this-section"></a>本節內容  
 [產生資料服務用戶端程式庫](generating-the-data-service-client-library-wcf-data-services.md)  
 描述如何產生以摘要為基礎[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]的用戶端程式庫和用戶端資料服務類別。  
  
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
 描述如何將控制項系結至[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]資料服務所傳回的摘要。  
  
 [呼叫服務作業](calling-service-operations-wcf-data-services.md)  
 說明如何使用用戶端程式庫呼叫服務作業。  
  
 [管理資料服務內容](managing-the-data-service-context-wcf-data-services.md)  
 說明用於管理用戶端程式庫行為的選項。  
  
 [使用二進位資料](working-with-binary-data-wcf-data-services.md)  
 說明如何存取及變更資料服務當做資料流傳回的二進位資料。  
  
## <a name="see-also"></a>另請參閱

- [定義 WCF Data Services](defining-wcf-data-services.md)
- [快速入門](getting-started-with-wcf-data-services.md)

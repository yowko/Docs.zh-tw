---
title: HOW TO：設定用戶端要求中的標頭 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 420b13df0cc9d3f89087e18b58a2b416ce0bab7f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975255"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>HOW TO：設定用戶端要求中的標頭 (WCF Data Services)
當您使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫來存取支援開放式資料通訊協定（OData）的資料服務時，用戶端程式庫會自動在傳送至資料服務的要求訊息中設定所需的 HTTP 標頭。 不過，在某些情況下，用戶端程式庫不知道要設定所需的訊息標頭，例如，當資料服務需要宣告架構的驗證或 Cookie 時。 如需詳細資訊，請參閱 [Securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication)。 在這些情況下，您必須在以要求訊息中手動設定訊息標頭，然後再傳送出去。 本主題中的範例會示範如何處理 <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> 事件，以便將新的標頭加入至要求訊息中，然後再傳送至資料服務。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。 您也可以使用在 OData 網站上發行的[Northwind 範例資料服務](https://go.microsoft.com/fwlink/?LinkId=187426);這個範例資料服務是唯讀的，而且嘗試儲存變更時，會傳回錯誤。 OData 網站上的範例資料服務允許匿名驗證。  
  
## <a name="example"></a>範例  
 下列範例會註冊 <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> 事件的處理常式，然後根據資料服務執行查詢。  
  
> [!NOTE]
> 當資料服務要求您手動設定每個要求的訊息標頭時，請考慮註冊 <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> 事件的處理常式，方法是，覆寫表示資料服務之實體容器中的 `OnContextCreated` 部分方法，在此情況下為 `NorthwindEntities`。  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>範例  
 下列方法會處理 <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> 事件，並將驗證標頭加入至要求中。  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>請參閱

- [保護 WCF 資料服務的安全](securing-wcf-data-services.md)
- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)

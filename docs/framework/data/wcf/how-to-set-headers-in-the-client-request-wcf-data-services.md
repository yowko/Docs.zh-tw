---
title: HOW TO：設定用戶端要求中的標頭 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
ms.openlocfilehash: 9267f0e5b68823516764891a40e1435c1325b77f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174338"
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>HOW TO：設定用戶端要求中的標頭 (WCF Data Services)
當您使用 WCF 資料服務用戶端庫訪問支援開放資料協定 （OData） 的資料服務時，用戶端庫會自動在發送到資料服務的請求消息中設置所需的 HTTP 標頭。 不過，在某些情況下，用戶端程式庫不知道要設定所需的訊息標頭，例如，當資料服務需要宣告架構的驗證或 Cookie 時。 如需詳細資訊，請參閱 [Securing WCF Data Services](securing-wcf-data-services.md#clientAuthentication)。 在這些情況下，您必須在以要求訊息中手動設定訊息標頭，然後再傳送出去。 本主題中的範例會示範如何處理 <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> 事件，以便將新的標頭加入至要求訊息中，然後再傳送至資料服務。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF 資料服務快速啟動](quickstart-wcf-data-services.md)時，將創建此服務和用戶端資料類。 您還可以使用在 OData 網站上發佈的[北風示例資料服務](https://services.odata.org/Northwind/Northwind.svc/);此示例資料服務是唯讀的，嘗試保存更改將返回錯誤。 OData 網站上的示例資料服務允許匿名身份驗證。  
  
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
  
## <a name="see-also"></a>另請參閱

- [Securing WCF Data Services](securing-wcf-data-services.md)
- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)

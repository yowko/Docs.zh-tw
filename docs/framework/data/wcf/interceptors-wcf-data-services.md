---
title: 攔截器 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: 7decfdd738e71a01afa8cb32604953142b46e588
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790434"
---
# <a name="interceptors-wcf-data-services"></a>攔截器 (WCF 資料服務)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]讓應用程式攔截要求訊息，讓您可以將自訂邏輯加入至作業。 您可以使用這個自訂邏輯來驗證傳入訊息中的資料。 您還可以使用它進一步限制查詢要求的範圍，例如，以根據要求來插入自訂授權原則。  
  
 攔截由資料服務中特別屬性化的方法執行。 在訊息處理期間的適當時間點，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會呼叫這些方法。 攔截器是根據每個實體集來定義，而攔截器方法則無法接受來自要求的參數，例如服務作業可以。 查詢攔截器方法（在處理 HTTP GET 要求時呼叫）必須傳回 lambda 運算式，以判斷查詢結果是否應傳回攔截器實體集的實例。 資料服務會使用此運算式進一步精簡所要求的作業。 以下是查詢攔截器的定義範例。  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 如需詳細資訊，請參閱[如何：攔截資料服務訊息](how-to-intercept-data-service-messages-wcf-data-services.md)。  
  
 變更處理非查詢作業時呼叫的攔截器，必須傳回 `void` (在 Visual Basic 為 `Nothing`)。 變更攔截器方法必須接受下列兩個參數：  
  
1. 其類型相容於實體集實體類型的參數。 資料服務叫用變更攔截器時，此參數的值會反映出要求所傳送的實體資訊。  
  
2. 類型為 <xref:System.Data.Services.UpdateOperations> 的參數。 資料服務叫用變更攔截器時，此參數的值會反映出要求嘗試執行的作業。  
  
 以下是變更攔截器的定義範例。  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 如需詳細資訊，請參閱[如何：攔截資料服務訊息](how-to-intercept-data-service-messages-wcf-data-services.md)。  
  
 攔截支援的屬性如下。  
  
 **[QueryInterceptor(** *EntitySetName* **)]**  
 收到目標實體集資源的 HTTP GET 要求時，會呼叫套用 <xref:System.Data.Services.QueryInterceptorAttribute> 屬性的方法。 這些方法必須永遠以 `Expression<Func<T,bool>>` 形式傳回 Lambda 運算式。  
  
 **[ChangeInterceptor(** *EntitySetName* **)]**  
 當目標實體集資源收到 HTTP GET 要求以外的 HTTP 要求時，會呼叫套用 <xref:System.Data.Services.ChangeInterceptorAttribute> 屬性的方法。 這些方法必須永遠傳回 `void` (在 Visual Basic 中為 `Nothing`)。  
  
 如需詳細資訊，請參閱[如何：攔截資料服務訊息](how-to-intercept-data-service-messages-wcf-data-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [服務作業](service-operations-wcf-data-services.md)

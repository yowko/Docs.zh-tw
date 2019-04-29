---
title: WCF Web HTTP 錯誤處理
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 834c642e36e1551081dbe1f14529ed7596df1360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935482"
---
# <a name="wcf-web-http-error-handling"></a>WCF Web HTTP 錯誤處理
Windows Communication Foundation (WCF) Web HTTP 錯誤處理可讓您從指定的 HTTP 狀態碼，並傳回錯誤詳細資料，使用相同的格式與作業 （例如 XML 或 JSON） 的 WCF Web HTTP 服務傳回錯誤。  
  
## <a name="wcf-web-http-error-handling"></a>WCF Web HTTP 錯誤處理  
 <xref:System.ServiceModel.Web.WebFaultException> 類別會定義一個建構函式，供您指定 HTTP 狀態碼。 然後，這個狀態碼會傳回用戶端。 <xref:System.ServiceModel.Web.WebFaultException> 類別的泛型版本 <xref:System.ServiceModel.Web.WebFaultException%601> 可讓您傳回使用者定義的型別，其中包含已發生錯誤的相關資訊。 此自訂物件會使用作業指定的格式序列化，然後傳回用戶端。 下列範例示範如何傳回 HTTP 狀態碼。  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 下列範例示範如何傳回 HTTP 狀態碼，以及使用者定義型別中的額外資訊。 `MyErrorDetail` 是使用者定義的型別，其中包含有關已發生之錯誤的額外資訊。  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 前一個程式碼會傳回 HTTP 回應，附上禁止狀態碼與本文，而本文中會包含 `MyErrorDetails` 物件的執行個體。 `MyErrorDetails` 物件的格式取決於：  
  
- 服務作業所指定 `ResponseFormat` 或 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性之 <xref:System.ServiceModel.Web.WebInvokeAttribute> 參數的值。  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> 的值。  
  
- 透過存取 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> 之 <xref:System.ServiceModel.Web.OutgoingWebResponseContext> 屬性的值。  
  
 如需有關這些值如何影響作業的格式設定的詳細資訊，請參閱[WCF Web HTTP 格式化](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。  
  
 <xref:System.ServiceModel.Web.WebFaultException> 是一個 <xref:System.ServiceModel.FaultException>，因此可以針對公開 SOAP 端點以及 Web HTTP 端點的服務，用來當做服務的錯誤例外狀況程式撰寫模型。  
  
## <a name="see-also"></a>另請參閱

- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Web HTTP 格式化](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [定義並指定錯誤](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [處理例外狀況和失敗](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [傳送及接收錯誤](../../../../docs/framework/wcf/sending-and-receiving-faults.md)

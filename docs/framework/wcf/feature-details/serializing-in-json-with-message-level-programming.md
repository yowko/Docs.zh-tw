---
title: 使用訊息層級程式設計序列化 Json
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: fc2777d71376cc482b715898fa81ddf618bd8284
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186936"
---
# <a name="serializing-in-json-with-message-level-programming"></a>使用訊息層級程式設計序列化 Json
WCF 支援 JSON 格式的序列化資料。 本主題描述如何使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 來指示 WCF 序列化您的型別。  
  
## <a name="typed-message-programming"></a>具型別的訊息程式設計  
 將 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 或 <xref:System.ServiceModel.Web.WebGetAttribute> 套用至服務作業時會使用 <xref:System.ServiceModel.Web.WebInvokeAttribute>。 這兩個屬性可讓您指定 `RequestFormat` 和 `ResponseFormat`。 若要使用 JSON 要求和回應。 設定這兩種以`WebMessageFormat.Json`。  若要使用 JSON，您必須使用<xref:System.ServiceModel.WebHttpBinding>，它會自動設定<xref:System.ServiceModel.Description.WebHttpBehavior>。 如需有關 WCF 序列化的詳細資訊，請參閱 <<c0> [ 序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。 如需有關 JSON 和 WCF 的詳細資訊，請參閱 <<c0> [ 服務站-簡介至 RESTful 服務與 WCF](https://msdn.microsoft.com/magazine/dd315413.aspx)。  
  
> [!IMPORTANT]
>  使用 JSON 需要使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior>，但這兩者不支援 SOAP 通訊。 與通訊的服務<xref:System.ServiceModel.WebHttpBinding>並支援公開服務中繼資料，因此您不能使用 Visual Studio 的 [加入服務參考] 功能或 svcutil 命令列工具來產生用戶端 proxy。 如需詳細資訊，您可以透過程式設計方式呼叫的方式使用服務<xref:System.ServiceModel.WebHttpBinding>，請參閱 <<c2> [ 取用 REST 服務與 WCF 如何](https://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx)。  
  
## <a name="untyped-message-programming"></a>不具型別的訊息程式設計  
 直接使用不具型別的訊息物件時，您必須明確設定不具型別訊息上的屬性，以將其序列化為 JSON。 下列程式碼片段示範如何執行這項操作。  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>另請參閱

- [AJAX 整合與 JSON 支援](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [獨立 JSON 序列化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [JSON 序列化](../../../../docs/framework/wcf/samples/json-serialization.md)

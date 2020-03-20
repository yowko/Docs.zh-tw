---
title: 使用訊息層級程式設計序列化 Json
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 36459dbc0ddee883678a98a27f9abb74fde78e86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184489"
---
# <a name="serializing-in-json-with-message-level-programming"></a>使用訊息層級程式設計序列化 Json
WCF 支援 JSON 格式的序列化資料。 本主題描述如何使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 來指示 WCF 序列化您的型別。  
  
## <a name="typed-message-programming"></a>具型別的訊息程式設計  
 將 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 或 <xref:System.ServiceModel.Web.WebGetAttribute> 套用至服務作業時會使用 <xref:System.ServiceModel.Web.WebInvokeAttribute>。 這兩個屬性可讓您指定 `RequestFormat` 和 `ResponseFormat`。 使用 JSON 進行請求和回應。 將兩者設置為`WebMessageFormat.Json`。  要使用 JSON，必須使用 自動設定<xref:System.ServiceModel.WebHttpBinding>的<xref:System.ServiceModel.Description.WebHttpBehavior>。 有關 WCF 序列化的詳細資訊，請參閱[序列化和反序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。 有關 JSON 和 WCF 的詳細資訊，請參閱[服務站 - 使用 WCF 提供 RESTful 服務簡介](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf)。  
  
> [!IMPORTANT]
> 使用 JSON 需要使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior>，但這兩者不支援 SOAP 通訊。 與 通信的服務<xref:System.ServiceModel.WebHttpBinding>不支援公開服務中繼資料，因此您將無法使用 Visual Studio 的"添加服務參考"功能或 svcutil 命令列工具生成用戶端代理。 有關如何以程式設計方式調用使用<xref:System.ServiceModel.WebHttpBinding>的服務的詳細資訊，請參閱如何使用[WCF 使用 REST 服務](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf)。  
  
## <a name="untyped-message-programming"></a>不具型別的訊息程式設計  
 直接使用不具型別的訊息物件時，您必須明確設定不具型別訊息上的屬性，以將其序列化為 JSON。 下列程式碼片段示範如何執行這項操作。  
  
```csharp
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

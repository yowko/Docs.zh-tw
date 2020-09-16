---
title: 使用訊息層級程式設計序列化 Json
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 129b39051e5955181c33e6486ec3193383177e60
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546259"
---
# <a name="serializing-in-json-with-message-level-programming"></a>使用訊息層級程式設計序列化 Json
WCF 支援 JSON 格式的序列化資料。 本主題描述如何使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 來指示 WCF 序列化您的型別。  
  
## <a name="typed-message-programming"></a>具型別的訊息程式設計  
 將 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 或 <xref:System.ServiceModel.Web.WebGetAttribute> 套用至服務作業時會使用 <xref:System.ServiceModel.Web.WebInvokeAttribute>。 這兩個屬性可讓您指定 `RequestFormat` 和 `ResponseFormat`。 針對要求和回應使用 JSON。 將這兩個設定為 `WebMessageFormat.Json` 。  若要使用 JSON，您必須使用自動設定 <xref:System.ServiceModel.WebHttpBinding> 的 <xref:System.ServiceModel.Description.WebHttpBehavior> 。 如需 WCF 序列化的詳細資訊，請參閱 [序列化和還原序列化](serialization-and-deserialization.md)。 如需 JSON 和 WCF 的詳細資訊，請參閱 [Service 站-使用 WCF RESTful 服務的簡介](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf)。  
  
> [!IMPORTANT]
> 使用 JSON 需要使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior>，但這兩者不支援 SOAP 通訊。 與通訊的服務 <xref:System.ServiceModel.WebHttpBinding> 不支援公開服務中繼資料，因此您將無法使用 Visual Studio 的加入服務參考功能或 svcutil 命令列工具來產生用戶端 proxy。 如需如何以程式設計方式呼叫使用之服務的詳細資訊 <xref:System.ServiceModel.WebHttpBinding> ，請參閱 [如何使用 WCF 取用 REST 服務](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf)。  
  
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

- [AJAX 整合與 JSON 支援](ajax-integration-and-json-support.md)
- [獨立 JSON 序列化](stand-alone-json-serialization.md)
- [JSON 序列化](../samples/json-serialization.md)

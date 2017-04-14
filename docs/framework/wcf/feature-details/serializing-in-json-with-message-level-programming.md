---
title: "使用訊息層級程式設計序列化 Json | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 使用訊息層級程式設計序列化 Json
WCF 支援 JSON 格式的序列化資料。本主題描述如何使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 指示 WCF 來序列化您的型別。  
  
## 具型別的訊息程式設計  
 將 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 套用至服務作業時會使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>。這兩個屬性可讓您指定 `RequestFormat` 和 `ResponseFormat`。若要為要求和回應使用 JSON，請將這兩個屬性設定為 `WebMessageFormat.Json`。若要使用 JSON，您必須使用會自動設定 <xref:System.ServiceModel.Description.WebHttpBehavior> 的 <xref:System.ServiceModel.WebHttpBinding>。如需 WCF 序列化的詳細資訊，請參閱 [序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Windows Communication Foundation 中的序列化](http://msdn.microsoft.com/magazine/cc163569.aspx)。如需 JSON 和 WCF 的詳細資訊，請參閱 [RESTfull 服務與 WCF 簡介](http://msdn.microsoft.com/magazine/dd315413.aspx)、[在 .NET 3.5 中建立啟用 JSON 的 WCF 服務](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx)和 [WCF 中的 REST 概觀](http://msdn.microsoft.com/netframework/dd547388)。  
  
> [!IMPORTANT]
>  使用 JSON 需要使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior>，但這兩者不支援 SOAP 通訊。與 <xref:System.ServiceModel.WebHttpBinding> 進行通訊的服務不支援公開服務中繼資料，因此您無法使用 Visual Studio 的 \[加入服務參考\] 功能或 svcutil 命令列工具來產生用戶端 Proxy。如需如何使用 <xref:System.ServiceModel.WebHttpBinding> 以程式設計方式呼叫服務的詳細資訊，請參閱[如何透過 WCF 使用 REST 服務](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx)。  
  
## 不具型別的訊息程式設計  
 直接使用不具型別的訊息物件時，您必須明確設定不具型別訊息上的屬性，以將其序列化為 JSON。下列程式碼片段示範如何執行這項操作。  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
  
```  
  
## 請參閱  
 [AJAX 整合與 JSON 支援](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)   
 [獨立 JSON 序列化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)   
 [JSON 序列化](../../../../docs/framework/wcf/samples/json-serialization.md)
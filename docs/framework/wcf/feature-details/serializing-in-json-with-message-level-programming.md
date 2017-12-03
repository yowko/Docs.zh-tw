---
title: "使用訊息層級程式設計序列化 Json"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3967cd7002af8ff9aee4c4f25bd2422d2d0ea1ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="2f695-102">使用訊息層級程式設計序列化 Json</span><span class="sxs-lookup"><span data-stu-id="2f695-102">Serializing in Json with Message Level Programming</span></span>
<span data-ttu-id="2f695-103">WCF 支援 JSON 格式的序列化資料。</span><span class="sxs-lookup"><span data-stu-id="2f695-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="2f695-104">本主題描述如何使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 來指示 WCF 序列化您的型別。</span><span class="sxs-lookup"><span data-stu-id="2f695-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="2f695-105">具型別的訊息程式設計</span><span class="sxs-lookup"><span data-stu-id="2f695-105">Typed Message Programming</span></span>  
 <span data-ttu-id="2f695-106">將 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 或 <xref:System.ServiceModel.Web.WebGetAttribute> 套用至服務作業時會使用 <xref:System.ServiceModel.Web.WebInvokeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="2f695-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="2f695-107">這兩個屬性可讓您指定 `RequestFormat` 和 `ResponseFormat`。</span><span class="sxs-lookup"><span data-stu-id="2f695-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="2f695-108">若要為要求和回應使用 JSON，請將這兩個屬性設定為 `WebMessageFormat.Json`。</span><span class="sxs-lookup"><span data-stu-id="2f695-108">To use JSON for requests and responses set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="2f695-109">若要使用 JSON，您必須使用會自動設定 <xref:System.ServiceModel.WebHttpBinding> 的 <xref:System.ServiceModel.Description.WebHttpBehavior>。</span><span class="sxs-lookup"><span data-stu-id="2f695-109">In order to use JSON you must use the <xref:System.ServiceModel.WebHttpBinding> which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="2f695-110">如需有關 WCF 序列化的詳細資訊，請參閱：[序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)， [Windows Communication Foundation 序列化](http://msdn.microsoft.com/magazine/cc163569.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2f695-110">For more information about WCF serialization, see: [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Serialization in Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span></span> <span data-ttu-id="2f695-111">如需有關 JSON 和 WCF，請參閱[RESTfull 服務與 WCF](http://msdn.microsoft.com/magazine/dd315413.aspx)， [.NET 3.5 中建立具有 JSON 啟用 WCF 服務](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx)，和[WCF中的REST概觀](http://msdn.microsoft.com/netframework/dd547388).</span><span class="sxs-lookup"><span data-stu-id="2f695-111">For more information about JSON and WCF see [An Introduction to RESTfull Services with WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [Creating JSON-enabled WCF Services in .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), and [Overview of REST in WCF](http://msdn.microsoft.com/netframework/dd547388).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2f695-112">使用 JSON 需要使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior>，但這兩者不支援 SOAP 通訊。</span><span class="sxs-lookup"><span data-stu-id="2f695-112">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="2f695-113">與通訊的服務<xref:System.ServiceModel.WebHttpBinding>並支援公開服務中繼資料，因此無法使用 Visual Studio 加入服務參考 功能或 svcutil 命令列工具來產生用戶端 proxy。</span><span class="sxs-lookup"><span data-stu-id="2f695-113">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="2f695-114">如需如何以程式設計方式呼叫服務使用<xref:System.ServiceModel.WebHttpBinding>，請參閱[如何取用 REST 服務與 WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx)。</span><span class="sxs-lookup"><span data-stu-id="2f695-114">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="2f695-115">不具型別的訊息程式設計</span><span class="sxs-lookup"><span data-stu-id="2f695-115">Untyped Message Programming</span></span>  
 <span data-ttu-id="2f695-116">直接使用不具型別的訊息物件時，您必須明確設定不具型別訊息上的屬性，以將其序列化為 JSON。</span><span class="sxs-lookup"><span data-stu-id="2f695-116">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="2f695-117">下列程式碼片段示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="2f695-117">The following code snippet shows how to do this.</span></span>  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f695-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f695-118">See Also</span></span>  
 [<span data-ttu-id="2f695-119">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="2f695-119">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="2f695-120">獨立 JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="2f695-120">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="2f695-121">JSON 序列化</span><span class="sxs-lookup"><span data-stu-id="2f695-121">JSON Serialization</span></span>](../../../../docs/framework/wcf/samples/json-serialization.md)

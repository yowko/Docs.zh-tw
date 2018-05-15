---
title: WebContentTypeMapper 範例
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 89f13599e23f3e60ae4d9bc973debc436f46c147
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="9fe42-102">WebContentTypeMapper 範例</span><span class="sxs-lookup"><span data-stu-id="9fe42-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="9fe42-103">這個範例示範如何將新內容型別對應至 Windows Communication Foundation (WCF) 訊息本文格式。</span><span class="sxs-lookup"><span data-stu-id="9fe42-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="9fe42-104"><xref:System.ServiceModel.Description.WebHttpEndpoint>項目會插入 Web 訊息編碼器，可讓 WCF 接收 JSON、 XML 或原始二進位訊息，在相同的端點。</span><span class="sxs-lookup"><span data-stu-id="9fe42-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="9fe42-105">此編碼器會藉由尋找要求的 HTTP 內容型別來判定訊息的本文格式。</span><span class="sxs-lookup"><span data-stu-id="9fe42-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="9fe42-106">這個範例會介紹 <xref:System.ServiceModel.Channels.WebContentTypeMapper> 類別，以允許使用者控制內容型別與本文格式之間的對應。</span><span class="sxs-lookup"><span data-stu-id="9fe42-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="9fe42-107">WCF 提供的內容類型的一組預設對應。</span><span class="sxs-lookup"><span data-stu-id="9fe42-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="9fe42-108">例如，`application/json` 會對應至 JSON，而 `text/xml` 會對應至 XML。</span><span class="sxs-lookup"><span data-stu-id="9fe42-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="9fe42-109">未對應至 JSON 或 XML 的任何內容型別都會對應至原始二進位格式。</span><span class="sxs-lookup"><span data-stu-id="9fe42-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="9fe42-110">在某些案例中 (例如，Push-Style API)，服務開發人員不會控制由用戶端傳回的內容型別。</span><span class="sxs-lookup"><span data-stu-id="9fe42-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="9fe42-111">例如，用戶端可能會以 `text/javascript` 方式傳回 JSON，而不是以 `application/json` 方式。</span><span class="sxs-lookup"><span data-stu-id="9fe42-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="9fe42-112">在這種情況中，服務開發人員必須提供衍生自 <xref:System.ServiceModel.Channels.WebContentTypeMapper> 的型別來正確地處理指定的內容型別，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="9fe42-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9fe42-113">此型別必須覆寫 <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="9fe42-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="9fe42-114">此方法必須評估 `contentType` 引數，並傳回下列其中一個值：<xref:System.ServiceModel.Channels.WebContentFormat.Json>、<xref:System.ServiceModel.Channels.WebContentFormat.Xml>、<xref:System.ServiceModel.Channels.WebContentFormat.Raw> 或 <xref:System.ServiceModel.Channels.WebContentFormat.Default>。</span><span class="sxs-lookup"><span data-stu-id="9fe42-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="9fe42-115">傳回的 <xref:System.ServiceModel.Channels.WebContentFormat.Default> 會延後至預設的 Web 訊息編碼器對應。</span><span class="sxs-lookup"><span data-stu-id="9fe42-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="9fe42-116">在先前的範例程式碼中，`text/javascript` 內容型別會對應至 JSON，而所有其他對應都維持不變。</span><span class="sxs-lookup"><span data-stu-id="9fe42-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="9fe42-117">若要使用 `JsonContentTypeMapper` 類別，請在 Web.config 中使用以下內容：</span><span class="sxs-lookup"><span data-stu-id="9fe42-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9fe42-118">若要確認使用 JsonContentTypeMapper 的需求，從以上的組態檔中移除 contentTypeMapper 屬性。</span><span class="sxs-lookup"><span data-stu-id="9fe42-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="9fe42-119">嘗試使用 `text/javascript` 傳送 JSON 內容時，無法載入用戶端頁面。</span><span class="sxs-lookup"><span data-stu-id="9fe42-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9fe42-120">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="9fe42-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9fe42-121">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9fe42-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9fe42-122">中所述，建置此方案 WebContentTypeMapperSample.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9fe42-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9fe42-123">瀏覽至http://localhost/ServiceModelSamples/JCTMClientPage.htm（不要在瀏覽器從專案目錄開啟 JCTMClientPage.htm）。</span><span class="sxs-lookup"><span data-stu-id="9fe42-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9fe42-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9fe42-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9fe42-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9fe42-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9fe42-126">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="9fe42-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9fe42-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9fe42-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="9fe42-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fe42-128">See Also</span></span>

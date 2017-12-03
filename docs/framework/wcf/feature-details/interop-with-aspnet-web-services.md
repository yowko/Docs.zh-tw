---
title: "與 ASP.NET Web 服務的互通性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd30b2d62d3ecf21027c0225490da6f31113cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="77a2c-102">與 ASP.NET Web 服務的互通性</span><span class="sxs-lookup"><span data-stu-id="77a2c-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="77a2c-103">您可以藉由確定使用兩種技術所實作的服務都符合 WS-I Basic Profile 1.1 規格，以達到 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務和 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web 服務之間的互通性。</span><span class="sxs-lookup"><span data-stu-id="77a2c-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="77a2c-104">符合 WS-I Basic Profile 1.1 的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務可以透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 系統提供的繫結 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與 <xref:System.ServiceModel.BasicHttpBinding> 進行互通。</span><span class="sxs-lookup"><span data-stu-id="77a2c-104">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services that conform to WS-I Basic Profile 1.1 are interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="77a2c-105">請使用 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 選項將 <xref:System.Web.Services.WebService> 和 <xref:System.Web.Services.WebMethodAttribute> 屬性新增至介面 (而不是新增至類別)，並撰寫類別來實作介面，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="77a2c-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="77a2c-106">我們建議您使用這個選項，因為 <xref:System.Web.Services.WebService> 屬性的介面包含由可以透過不同類別重複使用的服務所執行的作業合約，而這些類別可以透過不同的方式來實作相同的合約。</span><span class="sxs-lookup"><span data-stu-id="77a2c-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="77a2c-107">請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性，讓訊息根據 SOAP 訊息的本文元素完整名稱傳送到方法，而不是根據 `SOAPAction` HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="77a2c-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="77a2c-108"> 會使用 `SOAPAction` HTTP 標頭來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="77a2c-108"> uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="77a2c-109">根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。</span><span class="sxs-lookup"><span data-stu-id="77a2c-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="77a2c-110">定義資料類型搭配使用時[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 服務採用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="77a2c-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], do the following:</span></span>  
  
-   <span data-ttu-id="77a2c-111">使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。</span><span class="sxs-lookup"><span data-stu-id="77a2c-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
-   <span data-ttu-id="77a2c-112">僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="77a2c-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="77a2c-113">請勿從 <xref:System.Xml.Serialization> 命名空間新增額外的屬性來控制如何將 .NET Framework 類別轉譯為 XML。</span><span class="sxs-lookup"><span data-stu-id="77a2c-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
-   <span data-ttu-id="77a2c-114">採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。</span><span class="sxs-lookup"><span data-stu-id="77a2c-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="77a2c-115">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務在訊息中使用的型別，可以由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式當做資料合約來處理，這樣就可以在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式的所有優點中得到更突出的效能。</span><span class="sxs-lookup"><span data-stu-id="77a2c-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, among other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
 <span data-ttu-id="77a2c-116">請避免使用 Internet Information Services (IIS) 提供的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="77a2c-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="77a2c-117"> 用戶端並不支援這些選項。</span><span class="sxs-lookup"><span data-stu-id="77a2c-117"> clients do not support them.</span></span> <span data-ttu-id="77a2c-118">如果必須保護某個服務的安全，請使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供的選項，因為這些選項都是依據標準通訊協定而建立，並且非常穩定好用。</span><span class="sxs-lookup"><span data-stu-id="77a2c-118">If a service must be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="77a2c-119">因載入 ServiceModel HttpModule 而造成的效能影響</span><span class="sxs-lookup"><span data-stu-id="77a2c-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="77a2c-120">在 .NET Framework 3.0 中，WCF `HttpModule` 是安裝在根 Web.config 檔案中，以便讓每個 ASP.NET 應用程式都啟用 WCF。</span><span class="sxs-lookup"><span data-stu-id="77a2c-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="77a2c-121">這可能會影響效能，所以，您可以移除 Web.config 檔的 `ServiceModel`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="77a2c-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="77a2c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77a2c-122">See Also</span></span>  
 [<span data-ttu-id="77a2c-123">如何： 設定 WCF 服務與 ASP.NET Web 服務用戶端交互操作</span><span class="sxs-lookup"><span data-stu-id="77a2c-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)

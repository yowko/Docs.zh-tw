---
title: 與 ASP.NET Web 服務的互通性
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 16e22a091b88d12abccb063d2407db82460458c6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638601"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="88ca2-102">與 ASP.NET Web 服務的互通性</span><span class="sxs-lookup"><span data-stu-id="88ca2-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="88ca2-103">之間的互通性[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]可藉由確保服務使用這兩種技術實作符合 ws-i Web 服務和 Windows Communication Foundation (WCF) Web 服務-Basic Profile 1.1 規格。</span><span class="sxs-lookup"><span data-stu-id="88ca2-103">Interoperability between [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] <span data-ttu-id="88ca2-104">Web 服務符合 WS-Basic Profile 1.1 會使用 WCF 系統提供繫結，與 WCF 用戶端互通<xref:System.ServiceModel.BasicHttpBinding>。</span><span class="sxs-lookup"><span data-stu-id="88ca2-104">Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="88ca2-105">請使用 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 選項將 <xref:System.Web.Services.WebService> 和 <xref:System.Web.Services.WebMethodAttribute> 屬性新增至介面 (而不是新增至類別)，並撰寫類別來實作介面，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="88ca2-105">Use [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="88ca2-106">我們建議您使用這個選項，因為 <xref:System.Web.Services.WebService> 屬性的介面包含由可以透過不同類別重複使用的服務所執行的作業合約，而這些類別可以透過不同的方式來實作相同的合約。</span><span class="sxs-lookup"><span data-stu-id="88ca2-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="88ca2-107">請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性，讓訊息根據 SOAP 訊息的本文元素完整名稱傳送到方法，而不是根據 `SOAPAction` HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="88ca2-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="88ca2-108">WCF 會使用`SOAPAction`路由傳送訊息的 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="88ca2-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="88ca2-109">根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。</span><span class="sxs-lookup"><span data-stu-id="88ca2-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="88ca2-110">定義資料類型與搭配使用時[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]採用 WCF 中的 Web 服務，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="88ca2-110">When defining a data type for use with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="88ca2-111">使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。</span><span class="sxs-lookup"><span data-stu-id="88ca2-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="88ca2-112">僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="88ca2-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="88ca2-113">請勿從 <xref:System.Xml.Serialization> 命名空間新增額外的屬性來控制如何將 .NET Framework 類別轉譯為 XML。</span><span class="sxs-lookup"><span data-stu-id="88ca2-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="88ca2-114">採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。</span><span class="sxs-lookup"><span data-stu-id="88ca2-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="88ca2-115">在訊息中使用的型別[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]可以當做資料合約處理 Web 服務，WCF 應用程式，撇開其他優點，產生較佳的效能，在 WCF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="88ca2-115">The types used in messages by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="88ca2-116">請避免使用 Internet Information Services (IIS) 提供的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="88ca2-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="88ca2-117">WCF 用戶端不支援它們。</span><span class="sxs-lookup"><span data-stu-id="88ca2-117">WCF clients do not support them.</span></span> <span data-ttu-id="88ca2-118">如果服務必須受到保護，請使用 WCF，因為這些選項是強固，而且會以標準的通訊協定為基礎所提供的選項。</span><span class="sxs-lookup"><span data-stu-id="88ca2-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="88ca2-119">因載入 ServiceModel HttpModule 而造成的效能影響</span><span class="sxs-lookup"><span data-stu-id="88ca2-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="88ca2-120">在 .NET Framework 3.0 中，WCF `HttpModule` 是安裝在根 Web.config 檔案中，以便讓每個 ASP.NET 應用程式都啟用 WCF。</span><span class="sxs-lookup"><span data-stu-id="88ca2-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="88ca2-121">這可能會影響效能，所以，您可以移除 Web.config 檔的 `ServiceModel`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="88ca2-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88ca2-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88ca2-122">See also</span></span>

- [<span data-ttu-id="88ca2-123">如何：設定 WCF 服務與 ASP.NET Web 服務用戶端交互操作</span><span class="sxs-lookup"><span data-stu-id="88ca2-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)

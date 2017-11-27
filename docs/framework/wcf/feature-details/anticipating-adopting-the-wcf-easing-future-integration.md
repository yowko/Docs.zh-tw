---
title: "預計採用 Windows Communication Foundation：簡化未來整合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f60b2566895acfd7d2b749729fab9c3f5deb20c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a><span data-ttu-id="830bb-102">預計採用 Windows Communication Foundation：簡化未來整合</span><span class="sxs-lookup"><span data-stu-id="830bb-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>
<span data-ttu-id="830bb-103">如果您正使用 ASP.NET，並且預期會在未來使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，此主題提供指引以確定新的 ASP.NET Web 服務與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式能夠順利搭配運作。</span><span class="sxs-lookup"><span data-stu-id="830bb-103">If you use ASP.NET today, and anticipate using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, this topic provides guidance to ensure that new ASP.NET Web services will work well together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="830bb-104">一般建議</span><span class="sxs-lookup"><span data-stu-id="830bb-104">General Recommendations</span></span>  
 <span data-ttu-id="830bb-105">任何新服務都採用 ASP.NET 2.0。</span><span class="sxs-lookup"><span data-stu-id="830bb-105">Adopt ASP.NET 2.0 for any new services.</span></span> <span data-ttu-id="830bb-106">如此一來就能使用新版本的改進與增強功能。</span><span class="sxs-lookup"><span data-stu-id="830bb-106">Doing so will provide access to the improvements and enhancements of the new version.</span></span> <span data-ttu-id="830bb-107">但是，也可能會發生在相同的應用程式中同時使用 ASP.NET 2.0 與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="830bb-107">However, it will also allow for the possibility of using ASP.NET 2.0 components together with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components in the same application.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="830bb-108">通訊協定</span><span class="sxs-lookup"><span data-stu-id="830bb-108">Protocols</span></span>  
 <span data-ttu-id="830bb-109">使用 ASP.NET 2.0 的新功能以驗證是否符合 WS-I Basic Profile 1.1：</span><span class="sxs-lookup"><span data-stu-id="830bb-109">Use ASP.NET 2.0’s new facility for validating conformity to the WS-I Basic Profile 1.1:</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="830bb-110">符合 WS-I Basic Profile 1.1 的 ASP.NET Web 服務可以藉由使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 預先定義繫結 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，能夠與 <xref:System.ServiceModel.BasicHttpBinding> 用戶端互通。</span><span class="sxs-lookup"><span data-stu-id="830bb-110">ASP.NET Web services that conform to WS-I Basic Profile 1.1 will be interoperable with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients by using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] predefined binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="830bb-111">服務開發</span><span class="sxs-lookup"><span data-stu-id="830bb-111">Service Development</span></span>  
 <span data-ttu-id="830bb-112">請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性讓訊息不根據 SOAPAction HTTP 標頭而根據 SOAP 訊息的本文元素完整名稱傳送到方法。</span><span class="sxs-lookup"><span data-stu-id="830bb-112">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the SOAPAction HTTP header.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="830bb-113"> 會使用 SOAPAction HTTP 標頭傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="830bb-113"> uses the SOAPAction HTTP header for routing messages.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="830bb-114">資料表示</span><span class="sxs-lookup"><span data-stu-id="830bb-114">Data Representation</span></span>  
 <span data-ttu-id="830bb-115">根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。</span><span class="sxs-lookup"><span data-stu-id="830bb-115">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="830bb-116">當定義要與在未來可能會採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 之 ASP.NET Web 服務一起使用的資料型別時，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="830bb-116">When defining a data type for use with ASP.NET Web services in anticipation of adopting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in the future, do the following:</span></span>  
  
1.  <span data-ttu-id="830bb-117">使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。</span><span class="sxs-lookup"><span data-stu-id="830bb-117">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
2.  <span data-ttu-id="830bb-118">僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="830bb-118">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="830bb-119">請勿從 <xref:System.Xml.Serialization> 命名空間新增其他屬性，以控制 .NET Framework 類別轉譯成 XML 的方式。</span><span class="sxs-lookup"><span data-stu-id="830bb-119">Do no add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
 <span data-ttu-id="830bb-120">採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。</span><span class="sxs-lookup"><span data-stu-id="830bb-120">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="830bb-121">ASP.NET Web 服務在訊息中使用的型別，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式能夠將其當做資料合約處理，提供除了其他益處以外更好的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="830bb-121">The types used in messages by ASP.NET Web services will be able to be processed as data contracts by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications, yielding, amongst other benefits, better performance in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="security"></a><span data-ttu-id="830bb-122">安全性</span><span class="sxs-lookup"><span data-stu-id="830bb-122">Security</span></span>  
 <span data-ttu-id="830bb-123">請避免使用 Internet Information Services (IIS) 提供的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="830bb-123">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="830bb-124"> 用戶端並不支援這些選項。</span><span class="sxs-lookup"><span data-stu-id="830bb-124"> clients do not support them.</span></span> <span data-ttu-id="830bb-125">如果需要保護服務安全，請使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供的選項，因為這些選項的用途更廣並且是根據標準通訊協定。</span><span class="sxs-lookup"><span data-stu-id="830bb-125">If a service needs to be secured, use the options provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because these options are richer and are based on standard protocols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="830bb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="830bb-126">See Also</span></span>  
 [<span data-ttu-id="830bb-127">預計採用 Windows Communication Foundation： 簡化未來移轉</span><span class="sxs-lookup"><span data-stu-id="830bb-127">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)

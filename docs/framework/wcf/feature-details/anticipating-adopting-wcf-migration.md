---
title: "預計採用 Windows Communication Foundation：簡化未來移轉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 375274cd1b67b6dc71d3e66e1c1f063a81db7d8e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="bf757-102">預計採用 Windows Communication Foundation：簡化未來移轉</span><span class="sxs-lookup"><span data-stu-id="bf757-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="bf757-103">為確保未來 ASP.NET 新應用程式更容易移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請遵循上述建議和下列建議。</span><span class="sxs-lookup"><span data-stu-id="bf757-103">To ensure an easier future migration of new ASP.NET applications to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="bf757-104">通訊協定</span><span class="sxs-lookup"><span data-stu-id="bf757-104">Protocols</span></span>  
 <span data-ttu-id="bf757-105">停用 ASP.NET 2.0 的 SOAP 1.2 支援：</span><span class="sxs-lookup"><span data-stu-id="bf757-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>    
      </webServices>  
     </system.web>   
</configuration>  
```  
  
 <span data-ttu-id="bf757-106">建議這樣做，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 需要符合不同通訊協定 (如 SOAP 1.1 和 SOAP 1.2) 的訊息經過不同端點。</span><span class="sxs-lookup"><span data-stu-id="bf757-106">Doing so is advisable because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="bf757-107">如果 ASP.NET 2.0 Web 服務設定為同時支援 SOAP 1.1 和 SOAP 1.2 (預設組態)，則無法移轉前進至原始位址上，一定會與 ASP.NET Web 服務的所有現有用戶端相容的單一 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點。</span><span class="sxs-lookup"><span data-stu-id="bf757-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="bf757-108">此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。</span><span class="sxs-lookup"><span data-stu-id="bf757-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="bf757-109">服務開發</span><span class="sxs-lookup"><span data-stu-id="bf757-109">Service Development</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="bf757-110"> 可藉由將 <xref:System.ServiceModel.ServiceContractAttribute> 套用至介面或類別，來定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="bf757-110"> allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="bf757-111">建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。</span><span class="sxs-lookup"><span data-stu-id="bf757-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="bf757-112">ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。</span><span class="sxs-lookup"><span data-stu-id="bf757-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="bf757-113">不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。</span><span class="sxs-lookup"><span data-stu-id="bf757-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="bf757-114">因為一般建議修改服務的命名空間預設值 http://tempuri.org，所以應該可以繼續使用 <xref:System.Web.Services.WebService> 屬性的 Namespace 參數，將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性套用至介面或類別，來定義 ASP.NET Web 服務。</span><span class="sxs-lookup"><span data-stu-id="bf757-114">Since it is generally advisable to modify the namespace of a service from the default value, http://tempuri.org, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="bf757-115">在定義這些介面的方法中，盡可能不使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="bf757-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="bf757-116">將它們的工作委派至其他類別。</span><span class="sxs-lookup"><span data-stu-id="bf757-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="bf757-117">然後，新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務型別也可以將它們的實質性工作委派至這些類別。</span><span class="sxs-lookup"><span data-stu-id="bf757-117">New [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="bf757-118">使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。</span><span class="sxs-lookup"><span data-stu-id="bf757-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="bf757-119">這樣做很重要，因為 ASP.NET 中作業的預設名稱與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供的預設名稱不同。</span><span class="sxs-lookup"><span data-stu-id="bf757-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="bf757-120">藉由提供明確名稱，可以避免依賴預設名稱。</span><span class="sxs-lookup"><span data-stu-id="bf757-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="bf757-121">不要實作使用多型方法的 ASP.NET Web 服務作業，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不支援使用多型方法的作業。</span><span class="sxs-lookup"><span data-stu-id="bf757-121">Do not implement ASP.NET Web service operations with polymorphic methods, because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="bf757-122">使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。</span><span class="sxs-lookup"><span data-stu-id="bf757-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="bf757-123">採用這個方法，會避免依賴 ASP.NET 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用相同的 SOAPAction 預設值。</span><span class="sxs-lookup"><span data-stu-id="bf757-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] being the same.</span></span>  
  
-   <span data-ttu-id="bf757-124">避免使用 SOAP 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="bf757-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="bf757-125">如果需要 SOAP 擴充功能，請判斷其用途是否為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 已提供的功能。</span><span class="sxs-lookup"><span data-stu-id="bf757-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="bf757-126">如果是這種情況，請重新考慮不立即採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的選項。</span><span class="sxs-lookup"><span data-stu-id="bf757-126">If that is indeed the case, then reconsider the choice to not adopt [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="bf757-127">狀態管理</span><span class="sxs-lookup"><span data-stu-id="bf757-127">State Management</span></span>  
 <span data-ttu-id="bf757-128">避免在服務中維護狀態。</span><span class="sxs-lookup"><span data-stu-id="bf757-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="bf757-129">維護狀態不僅容易損害應用程式的延展性，而且 ASP.NET 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的狀態管理機制也非常不同，儘管 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援 ASP.NET 相容性模式中的 ASP.NET 機制。</span><span class="sxs-lookup"><span data-stu-id="bf757-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are very different, although [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="bf757-130">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="bf757-130">Exception Handling</span></span>  
 <span data-ttu-id="bf757-131">在設計服務所傳送和接收資料型別的結構時，也請設計各種例外狀況類型的結構，這些是您希望向用戶端告知可能會在服務中發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf757-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="bf757-132">提供這些類別自我序列化為 XML 的能力：</span><span class="sxs-lookup"><span data-stu-id="bf757-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 <span data-ttu-id="bf757-133">然後，類別就可以用來為明確擲回的 <xref:System.Web.Services.Protocols.SoapException> 執行個體提供詳細資料：</span><span class="sxs-lookup"><span data-stu-id="bf757-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="bf757-134">這些例外狀況類別隨時可由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.FaultException%601> 類別重複使用，擲回新的 `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="bf757-134">These exception classes will be readily reusable with the[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="bf757-135">安全性</span><span class="sxs-lookup"><span data-stu-id="bf757-135">Security</span></span>  
 <span data-ttu-id="bf757-136">以下是一些安全性考量事項：</span><span class="sxs-lookup"><span data-stu-id="bf757-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="bf757-137">避免使用 ASP.NET 2.0 設定檔，因為服務移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時，使用它們會限制使用 ASP.NET 整合模式。</span><span class="sxs-lookup"><span data-stu-id="bf757-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
-   <span data-ttu-id="bf757-138">避免使用 ACL 控制存取服務，因為 ASP.NET Web 服務支援 ACL 使用 Internet Information Services (IIS)，但 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 卻不支援 (ASP.NET Web 服務仰賴 IIS 進行裝載，而 WCF 不一定要裝載於 IIS)。</span><span class="sxs-lookup"><span data-stu-id="bf757-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="bf757-139">考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。</span><span class="sxs-lookup"><span data-stu-id="bf757-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf757-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf757-140">See Also</span></span>  
 [<span data-ttu-id="bf757-141">預計採用 Windows Communication Foundation： 簡化未來整合</span><span class="sxs-lookup"><span data-stu-id="bf757-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

---
title: 預計採用 Windows Communication Foundation：簡化未來移轉
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: aeafc164d16d9dc60ad0b3012da292e9b0bb38b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490041"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="be83e-102">預計採用 Windows Communication Foundation：簡化未來移轉</span><span class="sxs-lookup"><span data-stu-id="be83e-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="be83e-103">若要確保更容易未來新增 ASP.NET 應用程式移轉至 WCF，請遵循上述建議，以及下列建議。</span><span class="sxs-lookup"><span data-stu-id="be83e-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="be83e-104">通訊協定</span><span class="sxs-lookup"><span data-stu-id="be83e-104">Protocols</span></span>  
 <span data-ttu-id="be83e-105">停用 ASP.NET 2.0 的 SOAP 1.2 支援：</span><span class="sxs-lookup"><span data-stu-id="be83e-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="be83e-106">如此一來是建議的因為 WCF 需要經過不同端點符合不同通訊協定，如 SOAP 1.1 和 SOAP 1.2 的訊息。</span><span class="sxs-lookup"><span data-stu-id="be83e-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="be83e-107">如果 ASP.NET 2.0 Web 服務設定為支援 SOAP 1.1 和 SOAP 1.2，它不可以是預設的設定，移轉至單一 WCF 端點一定會是原始位址的順向和相容的 ASP.NET Web 所有服務的現有用戶端。</span><span class="sxs-lookup"><span data-stu-id="be83e-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="be83e-108">此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。</span><span class="sxs-lookup"><span data-stu-id="be83e-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="be83e-109">服務開發</span><span class="sxs-lookup"><span data-stu-id="be83e-109">Service Development</span></span>  
 <span data-ttu-id="be83e-110">WCF 可讓您藉由套用定義服務合約<xref:System.ServiceModel.ServiceContractAttribute>至介面或類別。</span><span class="sxs-lookup"><span data-stu-id="be83e-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="be83e-111">建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。</span><span class="sxs-lookup"><span data-stu-id="be83e-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="be83e-112">ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。</span><span class="sxs-lookup"><span data-stu-id="be83e-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="be83e-113">不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。</span><span class="sxs-lookup"><span data-stu-id="be83e-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="be83e-114">因為它是一般建議修改預設值，從服務的命名空間http://tempuri.org，使用的命名空間參數<xref:System.Web.Services.WebService>屬性，所以應該可以繼續定義 ASP.NET Web 服務藉由套用<xref:System.ServiceModel.ServiceContractAttribute>介面或類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="be83e-114">Since it is generally advisable to modify the namespace of a service from the default value, http://tempuri.org, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
-   <span data-ttu-id="be83e-115">在定義這些介面的方法中，盡可能不使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="be83e-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="be83e-116">將它們的工作委派至其他類別。</span><span class="sxs-lookup"><span data-stu-id="be83e-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="be83e-117">新的 WCF 服務類型無法然後也其實質性工作委派至這些類別。</span><span class="sxs-lookup"><span data-stu-id="be83e-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
-   <span data-ttu-id="be83e-118">使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。</span><span class="sxs-lookup"><span data-stu-id="be83e-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="be83e-119">這樣做很重要，因為 ASP.NET 中作業的預設名稱是由 WCF 所提供的預設名稱不同。</span><span class="sxs-lookup"><span data-stu-id="be83e-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="be83e-120">藉由提供明確名稱，可以避免依賴預設名稱。</span><span class="sxs-lookup"><span data-stu-id="be83e-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
-   <span data-ttu-id="be83e-121">要使用多型方法，實作 ASP.NET Web 服務作業，因為 WCF 不支援使用多型方法的實作作業。</span><span class="sxs-lookup"><span data-stu-id="be83e-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
-   <span data-ttu-id="be83e-122">使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。</span><span class="sxs-lookup"><span data-stu-id="be83e-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="be83e-123">採用這個方法會避免依賴預設使用 ASP.NET 和 WCF 相同的 SOAPAction 值。</span><span class="sxs-lookup"><span data-stu-id="be83e-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
-   <span data-ttu-id="be83e-124">避免使用 SOAP 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="be83e-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="be83e-125">如果需要 SOAP 擴充功能，請判斷其被視為的目的是否由 WCF 所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="be83e-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="be83e-126">如果是這種情況，請重新考慮不立即採用 WCF 的選擇。</span><span class="sxs-lookup"><span data-stu-id="be83e-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="be83e-127">狀態管理</span><span class="sxs-lookup"><span data-stu-id="be83e-127">State Management</span></span>  
 <span data-ttu-id="be83e-128">避免在服務中維護狀態。</span><span class="sxs-lookup"><span data-stu-id="be83e-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="be83e-129">沒有維護狀態通常會危及應用程式，延展性不僅 ASP.NET 和 WCF 的狀態管理機制也非常不同，雖然 WCF 支援 ASP.NET 相容性模式中的 ASP.NET 機制。</span><span class="sxs-lookup"><span data-stu-id="be83e-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="be83e-130">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="be83e-130">Exception Handling</span></span>  
 <span data-ttu-id="be83e-131">在設計服務所傳送和接收資料型別的結構時，也請設計各種例外狀況類型的結構，這些是您希望向用戶端告知可能會在服務中發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="be83e-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="be83e-132">提供這些類別自我序列化為 XML 的能力：</span><span class="sxs-lookup"><span data-stu-id="be83e-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="be83e-133">然後，類別就可以用來為明確擲回的 <xref:System.Web.Services.Protocols.SoapException> 執行個體提供詳細資料：</span><span class="sxs-lookup"><span data-stu-id="be83e-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="be83e-134">這些例外狀況類別將會使用 WCF 可輕易地重複使用<xref:System.ServiceModel.FaultException%601>擲回新的類別 `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="be83e-134">These exception classes will be readily reusable with the WCF<xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="be83e-135">安全性</span><span class="sxs-lookup"><span data-stu-id="be83e-135">Security</span></span>  
 <span data-ttu-id="be83e-136">以下是一些安全性考量事項：</span><span class="sxs-lookup"><span data-stu-id="be83e-136">The following are some security recommendations.</span></span>  
  
-   <span data-ttu-id="be83e-137">避免使用 ASP.NET 2.0 設定檔，做為使用這些屬性會限制使用 ASP.NET 整合模式，如果服務已移轉至 WCF。</span><span class="sxs-lookup"><span data-stu-id="be83e-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
-   <span data-ttu-id="be83e-138">避免使用 Acl 控制存取服務，做為 ASP.NET Web 服務支援 Acl 使用 Internet Information Services (IIS)、 WCF 並不會因為 ASP.NET Web 服務仰賴 IIS 進行裝載，而且 WCF 不一定要在 IIS 中裝載。</span><span class="sxs-lookup"><span data-stu-id="be83e-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
-   <span data-ttu-id="be83e-139">考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。</span><span class="sxs-lookup"><span data-stu-id="be83e-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be83e-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be83e-140">See Also</span></span>  
 [<span data-ttu-id="be83e-141">預計採用 Windows Communication Foundation：簡化未來整合</span><span class="sxs-lookup"><span data-stu-id="be83e-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

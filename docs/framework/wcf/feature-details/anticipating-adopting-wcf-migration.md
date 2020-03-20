---
title: 預計採用 Windows Communication Foundation：簡化未來移轉
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185464"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="a394b-102">預計採用 Windows Communication Foundation：簡化未來移轉</span><span class="sxs-lookup"><span data-stu-id="a394b-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="a394b-103">為確保新的ASP.NET應用程式更容易將來遷移到 WCF，請遵循前面的建議以及以下建議。</span><span class="sxs-lookup"><span data-stu-id="a394b-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="a394b-104">通訊協定</span><span class="sxs-lookup"><span data-stu-id="a394b-104">Protocols</span></span>  
 <span data-ttu-id="a394b-105">停用 ASP.NET 2.0 的 SOAP 1.2 支援：</span><span class="sxs-lookup"><span data-stu-id="a394b-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="a394b-106">這樣做是可取的，因為 WCF 要求符合不同協定（如 SOAP 1.1 和 SOAP 1.2）的消息使用不同的終結點。</span><span class="sxs-lookup"><span data-stu-id="a394b-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="a394b-107">如果 ASP.NET 2.0 Web 服務配置為同時支援 SOAP 1.1 和 SOAP 1.2（這是預設配置），則無法將其向前遷移到原始位址的單個 WCF 終結點，該終結點肯定與所有ASP.NET Web 相容服務的現有用戶端。</span><span class="sxs-lookup"><span data-stu-id="a394b-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="a394b-108">此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。</span><span class="sxs-lookup"><span data-stu-id="a394b-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="a394b-109">服務開發</span><span class="sxs-lookup"><span data-stu-id="a394b-109">Service Development</span></span>  
 <span data-ttu-id="a394b-110">WCF 允許您通過將 服務協定應用於<xref:System.ServiceModel.ServiceContractAttribute>介面或類來定義服務協定。</span><span class="sxs-lookup"><span data-stu-id="a394b-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="a394b-111">建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。</span><span class="sxs-lookup"><span data-stu-id="a394b-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="a394b-112">ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。</span><span class="sxs-lookup"><span data-stu-id="a394b-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="a394b-113">不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。</span><span class="sxs-lookup"><span data-stu-id="a394b-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="a394b-114">由於通常建議使用`http://tempuri.org`<xref:System.Web.Services.WebService>屬性的 Namespace 參數修改服務的命名空間，因此應該繼續通過將<xref:System.ServiceModel.ServiceContractAttribute>該屬性應用於介面或類來定義ASP.NET Web 服務。</span><span class="sxs-lookup"><span data-stu-id="a394b-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="a394b-115">在定義這些介面的方法中，盡可能不使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="a394b-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="a394b-116">將它們的工作委派至其他類別。</span><span class="sxs-lookup"><span data-stu-id="a394b-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="a394b-117">然後，新的 WCF 服務類型也可以將其實質性工作委託給這些類。</span><span class="sxs-lookup"><span data-stu-id="a394b-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="a394b-118">使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。</span><span class="sxs-lookup"><span data-stu-id="a394b-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="a394b-119">這樣做很重要，因為ASP.NET操作的預設名稱與 WCF 提供的預設名稱不同。</span><span class="sxs-lookup"><span data-stu-id="a394b-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="a394b-120">藉由提供明確名稱，可以避免依賴預設名稱。</span><span class="sxs-lookup"><span data-stu-id="a394b-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="a394b-121">不要使用多態方法實現ASP.NET Web 服務操作，因為 WCF 不支援使用多態方法實現操作。</span><span class="sxs-lookup"><span data-stu-id="a394b-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="a394b-122">使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。</span><span class="sxs-lookup"><span data-stu-id="a394b-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="a394b-123">採用此方法將規避依賴于 ASP.NET 和 WCF 使用的預設 SOAPAction 值的解決方法。</span><span class="sxs-lookup"><span data-stu-id="a394b-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="a394b-124">避免使用 SOAP 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="a394b-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="a394b-125">如果需要 SOAP 擴展，則確定考慮擴展的目的是否為 WCF 已經提供的功能。</span><span class="sxs-lookup"><span data-stu-id="a394b-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="a394b-126">如果確實如此，那麼重新考慮不馬上採用WCF的選擇。</span><span class="sxs-lookup"><span data-stu-id="a394b-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="a394b-127">狀態管理</span><span class="sxs-lookup"><span data-stu-id="a394b-127">State Management</span></span>  
 <span data-ttu-id="a394b-128">避免在服務中維護狀態。</span><span class="sxs-lookup"><span data-stu-id="a394b-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="a394b-129">維護狀態不僅會損害應用程式的可伸縮性，而且ASP.NET和 WCF 的狀態管理機制也大不相同，儘管 WCF 確實支援ASP.NET相容性模式下的ASP.NET機制。</span><span class="sxs-lookup"><span data-stu-id="a394b-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="a394b-130">例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="a394b-130">Exception Handling</span></span>  
 <span data-ttu-id="a394b-131">在設計服務所傳送和接收資料型別的結構時，也請設計各種例外狀況類型的結構，這些是您希望向用戶端告知可能會在服務中發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a394b-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a394b-132">提供這些類別自我序列化為 XML 的能力：</span><span class="sxs-lookup"><span data-stu-id="a394b-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="a394b-133">然後，類別就可以用來為明確擲回的 <xref:System.Web.Services.Protocols.SoapException> 執行個體提供詳細資料：</span><span class="sxs-lookup"><span data-stu-id="a394b-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="a394b-134">這些異常類將很容易重用與 WCF<xref:System.ServiceModel.FaultException%601>類，以拋出一個新的`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="a394b-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="a394b-135">安全性</span><span class="sxs-lookup"><span data-stu-id="a394b-135">Security</span></span>  
 <span data-ttu-id="a394b-136">以下是一些安全性考量事項：</span><span class="sxs-lookup"><span data-stu-id="a394b-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="a394b-137">避免使用ASP.NET 2.0 設定檔，因為如果服務遷移到 WCF，使用這些設定檔將限制ASP.NET整合模式的使用。</span><span class="sxs-lookup"><span data-stu-id="a394b-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="a394b-138">避免使用 ACL 來控制對服務的訪問，因為 ASP.NET Web 服務支援使用 Internet 資訊服務 （IIS） 的 ACL），WCF 不支援，因為 ASP.NET Web 服務依賴于 IIS 進行託管，並且 WCF 不一定必須在 IIS 中託管。</span><span class="sxs-lookup"><span data-stu-id="a394b-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="a394b-139">考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。</span><span class="sxs-lookup"><span data-stu-id="a394b-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a394b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a394b-140">See also</span></span>

- [<span data-ttu-id="a394b-141">預計採用 Windows Communication Foundation：簡化未來整合</span><span class="sxs-lookup"><span data-stu-id="a394b-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

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
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>預計採用 Windows Communication Foundation：簡化未來移轉
若要確保更容易未來新增 ASP.NET 應用程式移轉至 WCF，請遵循上述建議，以及下列建議。  
  
## <a name="protocols"></a>通訊協定  
 停用 ASP.NET 2.0 的 SOAP 1.2 支援：  
  
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
  
 如此一來是建議的因為 WCF 需要經過不同端點符合不同通訊協定，如 SOAP 1.1 和 SOAP 1.2 的訊息。 如果 ASP.NET 2.0 Web 服務設定為支援 SOAP 1.1 和 SOAP 1.2，它不可以是預設的設定，移轉至單一 WCF 端點一定會是原始位址的順向和相容的 ASP.NET Web 所有服務的現有用戶端。 此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。  
  
## <a name="service-development"></a>服務開發  
 WCF 可讓您藉由套用定義服務合約<xref:System.ServiceModel.ServiceContractAttribute>至介面或類別。 建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。 ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。 不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。 因為它是一般建議修改預設值，從服務的命名空間http://tempuri.org，使用的命名空間參數<xref:System.Web.Services.WebService>屬性，所以應該可以繼續定義 ASP.NET Web 服務藉由套用<xref:System.ServiceModel.ServiceContractAttribute>介面或類別的屬性。  
  
-   在定義這些介面的方法中，盡可能不使用程式碼。 將它們的工作委派至其他類別。 新的 WCF 服務類型無法然後也其實質性工作委派至這些類別。  
  
-   使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     這樣做很重要，因為 ASP.NET 中作業的預設名稱是由 WCF 所提供的預設名稱不同。 藉由提供明確名稱，可以避免依賴預設名稱。  
  
-   要使用多型方法，實作 ASP.NET Web 服務作業，因為 WCF 不支援使用多型方法的實作作業。  
  
-   使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     採用這個方法會避免依賴預設使用 ASP.NET 和 WCF 相同的 SOAPAction 值。  
  
-   避免使用 SOAP 擴充功能。 如果需要 SOAP 擴充功能，請判斷其被視為的目的是否由 WCF 所提供的功能。 如果是這種情況，請重新考慮不立即採用 WCF 的選擇。  
  
## <a name="state-management"></a>狀態管理  
 避免在服務中維護狀態。 沒有維護狀態通常會危及應用程式，延展性不僅 ASP.NET 和 WCF 的狀態管理機制也非常不同，雖然 WCF 支援 ASP.NET 相容性模式中的 ASP.NET 機制。  
  
## <a name="exception-handling"></a>例外狀況處理  
 在設計服務所傳送和接收資料型別的結構時，也請設計各種例外狀況類型的結構，這些是您希望向用戶端告知可能會在服務中發生的例外狀況。  
  
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
  
 提供這些類別自我序列化為 XML 的能力：  
  
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
  
 然後，類別就可以用來為明確擲回的 <xref:System.Web.Services.Protocols.SoapException> 執行個體提供詳細資料：  
  
```  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 這些例外狀況類別將會使用 WCF 可輕易地重複使用<xref:System.ServiceModel.FaultException%601>擲回新的類別 `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>安全性  
 以下是一些安全性考量事項：  
  
-   避免使用 ASP.NET 2.0 設定檔，做為使用這些屬性會限制使用 ASP.NET 整合模式，如果服務已移轉至 WCF。  
  
-   避免使用 Acl 控制存取服務，做為 ASP.NET Web 服務支援 Acl 使用 Internet Information Services (IIS)、 WCF 並不會因為 ASP.NET Web 服務仰賴 IIS 進行裝載，而且 WCF 不一定要在 IIS 中裝載。  
  
-   考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。  
  
## <a name="see-also"></a>另請參閱  
 [預計採用 Windows Communication Foundation：簡化未來整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

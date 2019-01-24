---
title: 預計採用 Windows Communication Foundation:簡化未來移轉
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 41deb6cb982e65b2af054840cdcb84e3d1db3451
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695253"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>預計採用 Windows Communication Foundation:簡化未來移轉
若要確保更容易未來新 ASP.NET 應用程式移轉至 WCF，請遵循上述建議，以及下列建議。  
  
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
  
 這種方式是建議的因為 WCF 要求訊息符合不同的通訊協定，如 SOAP 1.1 和 SOAP 1.2，請使用不同的端點。 如果 ASP.NET 2.0 Web 服務設定為支援 SOAP 1.1 和 SOAP 1.2 中，這是預設設定，則它不能移轉至單一 WCF 端點一定會是原始位址的順向可相容於所有的 ASP.NET Web服務的現有用戶端。 此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。  
  
## <a name="service-development"></a>服務開發  
 WCF 可讓您定義服務合約，藉由套用<xref:System.ServiceModel.ServiceContractAttribute>介面或類別。 建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。 ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。 不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。 因為它是一般建議修改預設值，從服務命名空間`http://tempuri.org`，使用的命名空間參數<xref:System.Web.Services.WebService>屬性，所以應該可以繼續定義 ASP.NET Web 服務，藉由套用<xref:System.ServiceModel.ServiceContractAttribute>介面或類別的屬性。  
  
-   在定義這些介面的方法中，盡可能不使用程式碼。 將它們的工作委派至其他類別。 新的 WCF 服務類型可能再也委派它們的實質性工作到這些類別。  
  
-   使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     如此一來很重要，因為 ASP.NET 中作業的預設名稱是由 WCF 所提供的預設名稱不同。 藉由提供明確名稱，可以避免依賴預設名稱。  
  
-   不會實作 ASP.NET Web 服務作業使用多型方法，因為 WCF 不支援使用多型方法的實作的作業。  
  
-   使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     這種方式會避免依賴預設使用 ASP.NET 和 WCF 相同的 SOAPAction 值。  
  
-   避免使用 SOAP 擴充功能。 如果 SOAP 擴充功能是必要的然後判斷它們會被視為的目的是已由 WCF 所提供的功能。 如果是這種情況，請重新考慮不立即採用 WCF 的選擇。  
  
## <a name="state-management"></a>狀態管理  
 避免在服務中維護狀態。 不只會維護狀態容易損害應用程式的延展性，但 ASP.NET 和 WCF 的狀態管理機制也非常不同，雖然 WCF 在 ASP.NET 相容性模式中支援 ASP.NET 機制。  
  
## <a name="exception-handling"></a>例外狀況處理  
 在設計服務所傳送和接收資料型別的結構時，也請設計各種例外狀況類型的結構，這些是您希望向用戶端告知可能會在服務中發生的例外狀況。  
  
```csharp  
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
  
 然後，類別就可以用來為明確擲回的 <xref:System.Web.Services.Protocols.SoapException> 執行個體提供詳細資料：  
  
```csharp  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 這些例外狀況類別將會立即可重複使用利用 WCF<xref:System.ServiceModel.FaultException%601>擲回新的類別 `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>安全性  
 以下是一些安全性考量事項：  
  
-   避免使用 ASP.NET 2.0 設定檔，以使用它們會限制使用 ASP.NET 整合模式，如果服務已移轉至 WCF。  
  
-   請避免使用 Acl 來控制存取服務，ASP.NET Web 服務支援 Acl 使用 Internet Information Services (IIS)，WCF 則否，因為 ASP.NET Web 服務仰賴 IIS 進行裝載，而 WCF 不一定要裝載在 IIS 中。  
  
-   考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。  
  
## <a name="see-also"></a>另請參閱
- [預計採用 Windows Communication Foundation:簡化未來整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

---
title: 預計採用 Windows Communication Foundation：簡化未來移轉
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: bf3155f19e42787746d59ce7b593273522e2840a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245051"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>預計採用 Windows Communication Foundation：簡化未來移轉

為了確保未來能夠更輕鬆地將新的 ASP.NET 應用程式遷移至 WCF，請遵循上述建議以及下列建議。  
  
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
  
 這麼做是建議的做法，因為 WCF 要求訊息必須符合不同的通訊協定，例如 SOAP 1.1 和 SOAP 1.2，才能使用不同的端點。 如果 ASP.NET 2.0 Web 服務設定為支援 SOAP 1.1 和 SOAP 1.2 （這是預設設定），則無法將它向前遷移至原始位址上的單一 WCF 端點，而該端點一定會與所有 ASP.NET Web 服務的現有用戶端相容。 此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。  
  
## <a name="service-development"></a>服務開發  

 WCF 可讓您藉由將套用 <xref:System.ServiceModel.ServiceContractAttribute> 至介面或類別來定義服務合約。 建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。 ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。 不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。 由於一般建議從預設值修改服務的命名空間，因此 `http://tempuri.org` ，請使用屬性的命名空間參數 <xref:System.Web.Services.WebService> ，將屬性（attribute）套用 <xref:System.ServiceModel.ServiceContractAttribute> 至介面或類別，以繼續定義 ASP.NET Web 服務。  
  
- 在定義這些介面的方法中，盡可能不使用程式碼。 將它們的工作委派至其他類別。 新的 WCF 服務類型也可以將其實體工作委派給這些類別。  
  
- 使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     這麼做很重要，因為 ASP.NET 中作業的預設名稱與 WCF 所提供的預設名稱不同。 藉由提供明確名稱，可以避免依賴預設名稱。  
  
- 請勿使用多型方法來執行 ASP.NET Web 服務作業，因為 WCF 不支援使用多型方法來執行作業。  
  
- 使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     採用這種方法，將會規避必須依賴 ASP.NET 和 WCF 所使用的預設 SOAPAction 值。  
  
- 避免使用 SOAP 擴充功能。 如果需要 SOAP 擴充功能，請判斷其所要考慮的目的是否為 WCF 已提供的功能。 如果是這種情況，則請重新考慮不要立即採用 WCF 的選擇。  
  
## <a name="state-management"></a>狀態管理  

 避免在服務中維護狀態。 維護狀態不僅會危及應用程式的擴充性，而且 ASP.NET 和 WCF 的狀態管理機制也非常不同，但 WCF 支援 ASP.NET 相容性模式中的 ASP.NET 機制。  
  
## <a name="exception-handling"></a>例外狀況處理  

 在設計服務所傳送和接收資料型別的結構時，也請設計各種例外狀況類型的結構，這些是您希望向用戶端告知可能會在服務中發生的例外狀況。  
  
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
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 這些例外狀況類別可立即與 WCF 類別重複使用 <xref:System.ServiceModel.FaultException%601> ，以擲回新的 `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>安全性  

 以下是一些安全性考量事項：  
  
- 避免使用 ASP.NET 2.0 設定檔，因為如果服務已遷移至 WCF，則使用它們會限制 ASP.NET 整合模式的使用。  
  
- 請避免使用 Acl 來控制對服務的存取，因為 ASP.NET Web 服務支援使用 Internet Information Services (IIS) 的 Acl，但 WCF 並不支援，因為 ASP.NET Web 服務相依于 IIS 來裝載，而且 WCF 不一定要裝載于 IIS 中。  
  
- 考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。  
  
## <a name="see-also"></a>另請參閱

- [預計採用 Windows Communication Foundation：簡化未來整合](anticipating-adopting-the-wcf-easing-future-integration.md)

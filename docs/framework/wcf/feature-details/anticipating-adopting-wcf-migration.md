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
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>預計採用 Windows Communication Foundation：簡化未來移轉
為確保新的ASP.NET應用程式更容易將來遷移到 WCF，請遵循前面的建議以及以下建議。  
  
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
  
 這樣做是可取的，因為 WCF 要求符合不同協定（如 SOAP 1.1 和 SOAP 1.2）的消息使用不同的終結點。 如果 ASP.NET 2.0 Web 服務配置為同時支援 SOAP 1.1 和 SOAP 1.2（這是預設配置），則無法將其向前遷移到原始位址的單個 WCF 終結點，該終結點肯定與所有ASP.NET Web 相容服務的現有用戶端。 此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。  
  
## <a name="service-development"></a>服務開發  
 WCF 允許您通過將 服務協定應用於<xref:System.ServiceModel.ServiceContractAttribute>介面或類來定義服務協定。 建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。 ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。 不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。 由於通常建議使用`http://tempuri.org`<xref:System.Web.Services.WebService>屬性的 Namespace 參數修改服務的命名空間，因此應該繼續通過將<xref:System.ServiceModel.ServiceContractAttribute>該屬性應用於介面或類來定義ASP.NET Web 服務。  
  
- 在定義這些介面的方法中，盡可能不使用程式碼。 將它們的工作委派至其他類別。 然後，新的 WCF 服務類型也可以將其實質性工作委託給這些類。  
  
- 使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     這樣做很重要，因為ASP.NET操作的預設名稱與 WCF 提供的預設名稱不同。 藉由提供明確名稱，可以避免依賴預設名稱。  
  
- 不要使用多態方法實現ASP.NET Web 服務操作，因為 WCF 不支援使用多態方法實現操作。  
  
- 使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     採用此方法將規避依賴于 ASP.NET 和 WCF 使用的預設 SOAPAction 值的解決方法。  
  
- 避免使用 SOAP 擴充功能。 如果需要 SOAP 擴展，則確定考慮擴展的目的是否為 WCF 已經提供的功能。 如果確實如此，那麼重新考慮不馬上採用WCF的選擇。  
  
## <a name="state-management"></a>狀態管理  
 避免在服務中維護狀態。 維護狀態不僅會損害應用程式的可伸縮性，而且ASP.NET和 WCF 的狀態管理機制也大不相同，儘管 WCF 確實支援ASP.NET相容性模式下的ASP.NET機制。  
  
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
  
 這些異常類將很容易重用與 WCF<xref:System.ServiceModel.FaultException%601>類，以拋出一個新的`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>安全性  
 以下是一些安全性考量事項：  
  
- 避免使用ASP.NET 2.0 設定檔，因為如果服務遷移到 WCF，使用這些設定檔將限制ASP.NET整合模式的使用。  
  
- 避免使用 ACL 來控制對服務的訪問，因為 ASP.NET Web 服務支援使用 Internet 資訊服務 （IIS） 的 ACL），WCF 不支援，因為 ASP.NET Web 服務依賴于 IIS 進行託管，並且 WCF 不一定必須在 IIS 中託管。  
  
- 考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。  
  
## <a name="see-also"></a>另請參閱

- [預計採用 Windows Communication Foundation：簡化未來整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

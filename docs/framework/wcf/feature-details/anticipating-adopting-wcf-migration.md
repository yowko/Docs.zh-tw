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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ecac6917d47604aa66e9cdc0d845e76ad2de5d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>預計採用 Windows Communication Foundation：簡化未來移轉
為確保未來 ASP.NET 新應用程式更容易移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，請遵循上述建議和下列建議。  
  
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
  
 建議這樣做，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 需要符合不同通訊協定 (如 SOAP 1.1 和 SOAP 1.2) 的訊息經過不同端點。 如果 ASP.NET 2.0 Web 服務設定為同時支援 SOAP 1.1 和 SOAP 1.2 (預設組態)，則無法移轉前進至原始位址上，一定會與 ASP.NET Web 服務的所有現有用戶端相容的單一 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 端點。 此外，選擇 SOAP 1.2 而非 1.1，也會嚴重限制服務的用戶端群。  
  
## <a name="service-development"></a>服務開發  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可藉由將 <xref:System.ServiceModel.ServiceContractAttribute> 套用至介面或類別，來定義服務合約。 建議將此屬性套用至介面而非類別，因為這樣做會建立可由任意類別數目以各種方式實作的合約定義。 ASP.NET 2.0 支援將 <xref:System.Web.Services.WebService> 屬性套用至介面和類別。 不過，如上述，ASP.NET 2.0 中有缺失，當 <xref:System.Web.Services.WebService> 屬性套用至介面而非類別時，該屬性的 Namespace 參數會沒有作用。 因為一般建議修改服務的命名空間預設值 http://tempuri.org，所以應該可以繼續使用 <xref:System.Web.Services.WebService> 屬性的 Namespace 參數，將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性套用至介面或類別，來定義 ASP.NET Web 服務。  
  
-   在定義這些介面的方法中，盡可能不使用程式碼。 將它們的工作委派至其他類別。 然後，新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務型別也可以將它們的實質性工作委派至這些類別。  
  
-   使用 `MessageName` 的 <xref:System.Web.Services.WebMethodAttribute> 參數，為服務的作業提供明確名稱。  
  
    ```  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     這樣做很重要，因為 ASP.NET 中作業的預設名稱與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供的預設名稱不同。 藉由提供明確名稱，可以避免依賴預設名稱。  
  
-   不要實作使用多型方法的 ASP.NET Web 服務作業，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不支援使用多型方法的作業。  
  
-   使用 <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute>，為用來將 HTTP 要求傳送至方法的 SOAPAction HTTP 標頭，提供明確值。  
  
    ```  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     採用這個方法，會避免依賴 ASP.NET 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 使用相同的 SOAPAction 預設值。  
  
-   避免使用 SOAP 擴充功能。 如果需要 SOAP 擴充功能，請判斷其用途是否為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 已提供的功能。 如果是這種情況，請重新考慮不立即採用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的選項。  
  
## <a name="state-management"></a>狀態管理  
 避免在服務中維護狀態。 維護狀態不僅容易損害應用程式的延展性，而且 ASP.NET 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的狀態管理機制也非常不同，儘管 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援 ASP.NET 相容性模式中的 ASP.NET 機制。  
  
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
  
 這些例外狀況類別隨時可由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.FaultException%601> 類別重複使用，擲回新的 `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>安全性  
 以下是一些安全性考量事項：  
  
-   避免使用 ASP.NET 2.0 設定檔，因為服務移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時，使用它們會限制使用 ASP.NET 整合模式。  
  
-   避免使用 ACL 控制存取服務，因為 ASP.NET Web 服務支援 ACL 使用 Internet Information Services (IIS)，但 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 卻不支援 (ASP.NET Web 服務仰賴 IIS 進行裝載，而 WCF 不一定要裝載於 IIS)。  
  
-   考慮使用 ASP.NET 2.0 角色提供者，來授權存取服務資源。  
  
## <a name="see-also"></a>另請參閱  
 [預計採用 Windows Communication Foundation： 簡化未來整合](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)

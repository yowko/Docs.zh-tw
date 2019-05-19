---
title: 與 ASP.NET Web 服務的互通性
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: c1b027eda315a76778e772235dc5f66e03c9d83e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875552"
---
# <a name="interoperability-with-aspnet-web-services"></a>與 ASP.NET Web 服務的互通性
ASP.NET Web 服務和 Windows Communication Foundation (WCF) Web 服務之間的互通性可藉由確保服務使用這兩種技術實作符合 ws-i-Basic Profile 1.1 規格。 ASP.NET Web 服務符合 WS-Basic Profile 1.1 會使用 WCF 系統提供繫結，與 WCF 用戶端互通<xref:System.ServiceModel.BasicHttpBinding>。  
  
 請使用 [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] 選項將 <xref:System.Web.Services.WebService> 和 <xref:System.Web.Services.WebMethodAttribute> 屬性新增至介面 (而不是新增至類別)，並撰寫類別來實作介面，如下列範例程式碼所示。  
  
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
  
 我們建議您使用這個選項，因為 <xref:System.Web.Services.WebService> 屬性的介面包含由可以透過不同類別重複使用的服務所執行的作業合約，而這些類別可以透過不同的方式來實作相同的合約。  
  
 請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性，讓訊息根據 SOAP 訊息的本文元素完整名稱傳送到方法，而不是根據 `SOAPAction` HTTP 標頭。 WCF 會使用`SOAPAction`路由傳送訊息的 HTTP 標頭。  
  
 根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。 當預期採用 WCF 定義與 ASP.NETWeb 服務搭配使用的資料類型，執行下列作業：  
  
- 使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。  
  
- 僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。 請勿從 <xref:System.Xml.Serialization> 命名空間新增額外的屬性來控制如何將 .NET Framework 類別轉譯為 XML。  
  
- 採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。 在訊息中的 ASP.NET Web 服務所使用的類型可以處理當做資料合約，WCF 應用程式產生，撇開其他優點，更好的效能，在 WCF 應用程式。  
  
 請避免使用 Internet Information Services (IIS) 提供的驗證選項。 WCF 用戶端不支援它們。 如果服務必須受到保護，請使用 WCF，因為這些選項是強固，而且會以標準的通訊協定為基礎所提供的選項。  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>因載入 ServiceModel HttpModule 而造成的效能影響  
 在 .NET Framework 3.0 中，WCF `HttpModule` 是安裝在根 Web.config 檔案中，以便讓每個 ASP.NET 應用程式都啟用 WCF。 這可能會影響效能，所以，您可以移除 Web.config 檔的 `ServiceModel`，如下列範例所示。  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>另請參閱

- [如何：設定 WCF 服務與 ASP.NET Web 服務用戶端交互操作](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)

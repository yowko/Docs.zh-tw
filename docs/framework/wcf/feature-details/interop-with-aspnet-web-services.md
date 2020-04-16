---
title: 與 ASP.NET Web 服務的互通性
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464096"
---
# <a name="interoperability-with-aspnet-web-services"></a>與 ASP.NET Web 服務的互通性
ASP.NET Web 服務和 Windows 通訊基礎 (WCF) Web 服務之間的互通性可以通過確保使用這兩種技術實現的服務符合 WS-I 基本配置檔 1.1 規範來實現。 ASP.NET符合 WS-I 基本設定檔 1.1 的 Web 服務透過使用 WCF 系統提供的<xref:System.ServiceModel.BasicHttpBinding>結合與 WCF 用戶端互通 。  
  
 使用 ASP.NET 2.0 選項<xref:System.Web.Services.WebService>將<xref:System.Web.Services.WebMethodAttribute>和 屬性添加到介面而不是類,並編寫一個類來實現介面,如以下示例代碼所示。  
  
```csharp
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
  
 請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性，讓訊息根據 SOAP 訊息的本文元素完整名稱傳送到方法，而不是根據 `SOAPAction` HTTP 標頭。 WCF`SOAPAction`使用 HTTP 標頭路由消息。  
  
 根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。 在定義資料類型以用於 ASP.NETWeb 服務以預期採用 WCF 時,執行以下操作:  
  
- 使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。  
  
- 僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。 請勿從 <xref:System.Xml.Serialization> 命名空間新增額外的屬性來控制如何將 .NET Framework 類別轉譯為 XML。  
  
- 採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。 ASP.NET Web 服務在消息中使用的類型可以由 WCF 應用程式作為數據協定進行處理,從而在 WCF 應用程式中產生更好的性能。  
  
 請避免使用 Internet Information Services (IIS) 提供的驗證選項。 WCF 用戶端不支持它們。 如果必須保護服務,請使用 WCF 提供的選項,因為這些選項是健壯的,並且基於標準協定。  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>因載入 ServiceModel HttpModule 而造成的效能影響  
 在 .NET Framework 3.0 中，WCF `HttpModule` 是安裝在根 Web.config 檔案中，以便讓每個 ASP.NET 應用程式都啟用 WCF。 這可能會影響效能，所以，您可以移除 Web.config 檔的 `ServiceModel`，如下列範例所示。  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>另請參閱

- [HOW TO：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)

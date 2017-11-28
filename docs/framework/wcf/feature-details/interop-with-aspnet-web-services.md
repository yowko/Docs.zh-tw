---
title: "與 ASP.NET Web 服務的互通性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 933d1bdac8f6e3a9e2bec5278fe398696131678a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="interoperability-with-aspnet-web-services"></a>與 ASP.NET Web 服務的互通性
您可以藉由確定使用兩種技術所實作的服務都符合 WS-I Basic Profile 1.1 規格，以達到 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務和 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web 服務之間的互通性。 符合 WS-I Basic Profile 1.1 的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務可以透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 系統提供的繫結 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 與 <xref:System.ServiceModel.BasicHttpBinding> 進行互通。  
  
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
  
 請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性，讓訊息根據 SOAP 訊息的本文元素完整名稱傳送到方法，而不是根據 `SOAPAction` HTTP 標頭。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 `SOAPAction` HTTP 標頭來傳送訊息。  
  
 根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。 定義資料類型搭配使用時[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 服務採用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，執行下列動作：  
  
-   使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。  
  
-   僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。 請勿從 <xref:System.Xml.Serialization> 命名空間新增額外的屬性來控制如何將 .NET Framework 類別轉譯為 XML。  
  
-   採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務在訊息中使用的型別，可以由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式當做資料合約來處理，這樣就可以在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式的所有優點中得到更突出的效能。  
  
 請避免使用 Internet Information Services (IIS) 提供的驗證選項。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端並不支援這些選項。 如果必須保護某個服務的安全，請使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所提供的選項，因為這些選項都是依據標準通訊協定而建立，並且非常穩定好用。  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>因載入 ServiceModel HttpModule 而造成的效能影響  
 在 .NET Framework 3.0 中，WCF `HttpModule` 是安裝在根 Web.config 檔案中，以便讓每個 ASP.NET 應用程式都啟用 WCF。 這可能會影響效能，所以，您可以移除 Web.config 檔的 `ServiceModel`，如下列範例所示。  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何： 設定 WCF 服務與 ASP.NET Web 服務用戶端交互操作](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)

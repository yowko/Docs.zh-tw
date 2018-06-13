---
title: 預計採用 Windows Communication Foundation：簡化未來整合
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f81e158a5e7f897307c0c6d376dfe01dac127ead
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489592"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>預計採用 Windows Communication Foundation：簡化未來整合
如果您正使用 ASP.NET，並且預期在未來使用 WCF，本主題提供指引以確定新的 ASP.NET Web 服務，將也與 WCF 應用程式正常運作。  
  
## <a name="general-recommendations"></a>一般建議  
 任何新服務都採用 ASP.NET 2.0。 如此一來就能使用新版本的改進與增強功能。 不過，也可讓在相同的應用程式中使用 ASP.NET 2.0 元件以及 WCF 元件的可能性。  
  
## <a name="protocols"></a>通訊協定  
 使用 ASP.NET 2.0 的新功能以驗證是否符合 WS-I Basic Profile 1.1：  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 符合 WS-I 的 ASP.NET Web 服務-Basic Profile 1.1 將會使用 WCF 用戶端互通使用 WCF 預先定義的繫結， <xref:System.ServiceModel.BasicHttpBinding>。  
  
## <a name="service-development"></a>服務開發  
 請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性讓訊息不根據 SOAPAction HTTP 標頭而根據 SOAP 訊息的本文元素完整名稱傳送到方法。 WCF 使用 SOAPAction HTTP 標頭路由訊息。  
  
## <a name="data-representation"></a>資料表示  
 根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。 定義時使用與 ASP.NET Web 服務的資料型別是採用 WCF 預期在未來，執行下列作業：  
  
1.  使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。  
  
2.  僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。 請勿從 <xref:System.Xml.Serialization> 命名空間新增其他屬性，以控制 .NET Framework 類別轉譯成 XML 的方式。  
  
 採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。 ASP.NET Web 服務在訊息中使用的類型將能夠處理做為資料合約，WCF 應用程式提供除了其他益處，WCF 應用程式較佳的效能。  
  
## <a name="security"></a>安全性  
 請避免使用 Internet Information Services (IIS) 提供的驗證選項。 WCF 用戶端不支援它們。 如果服務需要受到保護，請使用 WCF 提供的因為這些選項會有更豐富且標準通訊協定為基礎的選項。  
  
## <a name="see-also"></a>另請參閱  
 [預計採用 Windows Communication Foundation：簡化未來移轉](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)

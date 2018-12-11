---
title: 預計採用 Windows Communication Foundation:簡化未來整合
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: f4cc450b04fd05d390a1f41f3d14c19f4b23be29
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155141"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>預計採用 Windows Communication Foundation:簡化未來整合
如果您使用 ASP.NET，並預計在未來使用 WCF，本主題會提供指引以確定新的 ASP.NET Web 服務能夠順利與 WCF 應用程式。  
  
## <a name="general-recommendations"></a>一般建議  
 任何新服務都採用 ASP.NET 2.0。 如此一來就能使用新版本的改進與增強功能。 不過，這也能讓在相同的應用程式中使用 ASP.NET 2.0 元件，以及 WCF 元件的可能性。  
  
## <a name="protocols"></a>通訊協定  
 使用 ASP.NET 2.0 的新功能以驗證是否符合 WS-I Basic Profile 1.1：  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 ASP.NET Web 服務符合 WS-Basic Profile 1.1 會是互通的 WCF 用戶端搭配使用 WCF 預先定義繫結， <xref:System.ServiceModel.BasicHttpBinding>。  
  
## <a name="service-development"></a>服務開發  
 請避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 屬性讓訊息不根據 SOAPAction HTTP 標頭而根據 SOAP 訊息的本文元素完整名稱傳送到方法。 WCF 會使用 SOAPAction HTTP 標頭傳送訊息。  
  
## <a name="data-representation"></a>資料表示  
 根據預設，<xref:System.Xml.Serialization.XmlSerializer> 序列化型別的目標 XML 在語意上與 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化型別的目標 XML 是一樣的 (前提是 XML 的命名空間已明確定義)。 當定義未來預期的採用 WCF 與 ASP.NET Web 服務搭配使用的資料類型，執行下列作業：  
  
1.  使用 .NET Framework 類別，而不是 XML 結構描述來定義型別。  
  
2.  僅將 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 新增至類別，並使用後者明確定義該型別的命名空間。 請勿從 <xref:System.Xml.Serialization> 命名空間新增其他屬性，以控制 .NET Framework 類別轉譯成 XML 的方式。  
  
 採用這個方法之後，您稍後應該可以藉由新增 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute>，將 .NET 類別納入資料合約中，而不用特別提醒針對傳輸需要而序列化類別的目標 XML。 在訊息中的 ASP.NET Web 服務所使用的型別都能夠處理當做資料合約，WCF 應用程式產生，除了其他益處，較佳的效能，在 WCF 應用程式以外。  
  
## <a name="security"></a>安全性  
 請避免使用 Internet Information Services (IIS) 提供的驗證選項。 WCF 用戶端不支援它們。 如果服務需要受到保護，請使用 WCF，因為這些選項會更豐富，並會以標準的通訊協定為基礎所提供的選項。  
  
## <a name="see-also"></a>另請參閱  
 [預計採用 Windows Communication Foundation:簡化未來移轉](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)

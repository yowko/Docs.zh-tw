---
title: 建立 ASP.NET AJAX 的 WCF 服務
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 1f98a27197115c56686d593105f438fee633f34a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174144"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>建立 ASP.NET AJAX 的 WCF 服務
Microsoft ASP.NET AJAX 可讓您使用反應靈敏和熟悉的使用者介面項目，快速建立包含豐富使用者經驗的 Web 網頁。 ASP.NET AJAX 提供用戶端指令碼的程式庫，其中加入跨平台的 ECMAScript (JavaScript) 和動態 HTML (DHTML) 技術，並將它們與 ASP.NET 2.0 伺服器基礎的開發平台整合。 您可以使用 ASP.NET AJAX 功能來改善使用者經驗和 Web 應用程式的效率。  
  
 ASP.NET AJAX 包含內建的用戶端指令碼程式庫與伺服器元件，以提供您穩固的開發架構。 若要從 ASP.NET 頁面存取服務：一旦服務 URL 新增至頁面上的 ASP.NET 指令碼管理員控制項，服務作業可能會透過看起來與正常 JavaScript 函式呼叫沒兩樣的 JavaScript 程式碼來叫用。 請參閱[了解 ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475)有關在 AJAX 架構中的 Web 服務使用。  
  
 大部分的 Windows Communication Foundation (WCF) 服務可能會公開為與 ASP.NET AJAX 相容服務，藉由新增適當的 ASP.NET AJAX 端點。  
  
 如果您使用 Visual Studio，您可能使用預先建置的範本中所提供的啟用 AJAX 的 WCF 服務**加入新項目**對話方塊時使用 ASP.NET 網站或 Web 應用程式。  
  
 如果您不是使用 Visual Studio 範本，則您可以透過下列兩種方法來建立 ASP.NET AJAX 端點：  
  
-   使用動態主機啟動 (而不是透過任何組態) 來建立端點。 如果您不熟悉 WCF 組態系統的話，這是最基本的操作方式。 如需詳細資訊，請參閱[如何：不使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。  
  
-   啟用 AJAX 的端點加入至 WCF 服務使用的組態。 如需詳細資訊，請參閱[如何：使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。  
  
 Web 程式設計模型中所述[WCF Web HTTP 程式設計模型概觀](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)可搭配 ASP.NET AJAX 服務。 尤其是：  
  
-   您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性，在 HTTP GET 和 HTTP POST 動詞之間進行選擇。 如果使用方式正確的話，可能會大幅改善應用程式的效能。 如需詳細資訊，請參閱[如何：HTTP POST 和 HTTP GET 要求端點之間進行選擇 ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)。  
  
-   您可以使用 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> 屬性，讓您的服務傳回 XML 資料，而不是預設的 JavaScript Object Notation (JSON)。 使用 ASP.NET AJAX 架構來執行這項作業會導致 JavaScript 用戶端接收 XML DOM 物件。  
  
    > [!WARNING]
    >  您的作業必須將內容類型設定為文字/xml，才能讓此作業運作。 否則，JavaScript 用戶端將收到包含 XML 物件 (而非 XML DOM 物件) 的字串。  
  
     以下是內容類型設定正確時，傳回 XML 資料的範例：  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   如需與 ASP.NET AJAX 相容，則 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性 (Attribute) 上的其他屬性 (Property) 都將無法變更。 只要不違反 ASP.NET AJAX 呼叫慣例的話，就可以一直使用其他的 Web 程式設計模型方式。  
  
 更進階的案例需要了解 WCF 中的 AJAX 支援的其他詳細資料：  
  
-   若要了解傳送資料的方式未 AJAX 頁面用戶端與 WCF 服務使用 JavaScript，以及如需詳細資訊在.NET Framework 型別如何對應至 JavaScript 類型，請參閱[支援 JSON 和其他資料傳輸格式](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)。  
  
-   為了善加利用各項 ASP.NET 功能，例如 URL 驗證與存取 ASP.NET 工作階段資訊，您可能會想要透過組態來啟用 ASP.NET 相容性模式。  
  
 而不需要 ASP.NET AJAX 架構時，可能甚至取用 WCF 中的 AJAX 端點。 這種方式需要了解 WCF 中的 AJAX 支援的支援架構。 如需此架構的討論，請參閱 < [WCF Web HTTP 程式設計物件模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)。 如需示範此方法的程式碼範例，請參閱 <<c0> [ 含 JSON 和 XML 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [HOW TO：不使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [HOW TO：使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [HOW TO：在 ASP.NET AJAX 端點的 HTTP POST 和 HTTP GET 要求之間進行選擇](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)

---
title: HOW TO：在 ASP.NET AJAX 端點的 HTTP POST 和 HTTP GET 要求之間進行選擇
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184761"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>HOW TO：在 ASP.NET AJAX 端點的 HTTP POST 和 HTTP GET 要求之間進行選擇

Windows 通信基礎 （WCF） 允許您創建一個服務，該服務公開ASP.NET啟用 AJAX 的終結點，可以從用戶端網站上的 JavaScript 調用。 構建此類服務的基本過程在["如何：使用配置添加ASP.NETAJAX終結點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)以及如何[：添加ASP.NETAJAX終結點而不使用配置](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。  
  
 ASP.NET AJAX 支援使用 HTTP POST 和 HTTP GET 動詞 (預設為 HTTP POST) 的作業。 若要建立沒有任何副作用並傳回不常或永不變更的資料時，請改用 HTTP GET。 您可以快取 GET 作業的結果，也就是說，對相同作業的多次呼叫可能只需要對服務提出一次要求。 緩存不是由 WCF 完成的，但可以在任何級別（在使用者的瀏覽器、代理伺服器和其他級別）進行。如果要提高服務性能，緩存是有利的，但如果資料頻繁更改或操作執行某些操作，則緩存可能不可接受。  
  
 例如，如果您正在設計服務來管理使用者的音樂資料庫，負責依據專輯標題來查詢音樂創作者的作業就可以利用 GET 輕鬆得到想要的資料，但是將專輯新增至使用者個人收藏的作業則必須使用 POST 才行。  
  
 若要控制快取的存留期，請使用 <xref:System.ServiceModel.Web.OutgoingWebResponseContext> 型別。 例如，在設計可傳回每小時更新的氣象預報服務時，可以使用 GET 並將快取範圍限制在一小時以內，以避免服務的使用者存取到過時資料。  
  
 當您使用來自 ASP.NET AJAX 頁面 (使用指令碼管理員控制項) 的服務時，不論作業是使用 GET 或 POST，指令碼管理員機制都會確保發出正確的要求類型。  
  
 HTTP GET 作業會使用 POST 作業支援的所有輸入參數，包括複雜資料合約型別。 但是，在大部分情況下，建議您不要在 GET 作業中使用太多或太複雜的參數，因為這樣會降低快取效率。  
  
 本主題說明如何藉由將 <xref:System.ServiceModel.Web.WebGetAttribute> 或 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性新增至服務合約內的相關作業中，以便在 GET 和 POST 間進行選取。 運行服務所需的其他步驟（實現、配置和託管服務）與 WCF 中任何ASP.NET AJAX 服務所使用的步驟類似。  
  
 加上 <xref:System.ServiceModel.Web.WebGetAttribute> 標示的作業一律使用 GET 要求。 加上 <xref:System.ServiceModel.Web.WebInvokeAttribute> 標示，或是未加上任何這兩個屬性的作業，則會使用 POST 要求。 <xref:System.ServiceModel.Web.WebInvokeAttribute> 允許透過 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 屬性使用 GET 和 POST 以外的其他 HTTP 動詞 (例如 PUT 和 DELETE 等等)。 但是，ASP.NET AJAX 並不支援這些動詞。 如果您想要透過指令碼管理員控制項使用來自 ASP.NET 頁面的服務，請勿使用 <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> 屬性。  
  
 有關切換到 GET 的工作示例，請參閱基本[AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)示例。  
  
 有關使用 POST 的示例，請參閱[使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)的 AJAX 服務示例。  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>若要建立回應 HTTP GET 或 HTTP POST 要求的 WCF 服務
  
1. 定義具有帶有<xref:System.ServiceModel.ServiceContractAttribute>屬性標記的介面的基本 WCF 服務協定。 以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。 新增 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，以指定回應 HTTP GET 要求的作業。 您也可以新增 <xref:System.ServiceModel.Web.WebInvokeAttribute> 屬性，明確地指定 HTTP POST，或不指定屬性 (如此將預設為 HTTP POST)。
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. 使用 `IMusicService` 來實作 `MusicService` 服務合約。
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. 在應用程式中建立名為 service 且包含 .svc 副檔名的新檔案。 通過添加服務的相應[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令資訊來編輯此檔。 指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>將在[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令中使用，以自動設定ASP.NET AJAX 終結點。  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>若要呼叫服務  
  
1. 您可以透過瀏覽器，測試不包含任何用戶端程式碼的服務 GET 作業。 例如，如果服務在`http://example.com/service.svc`位址處配置，則鍵入`http://example.com/service.svc/LookUpArtist?album=SomeAlbum`瀏覽器網址列會調用該服務並導致下載或顯示回應。
  
2. 您可以使用包含 GET 作業的服務，方法就像您使用其他任何 ASP.NET AJAX 服務一樣，亦即在 ASP.NET AJAX 指令碼管理員控制項的指令碼集合中輸入服務 URL。 例如，請參閱[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)。
  
## <a name="see-also"></a>另請參閱

- [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)

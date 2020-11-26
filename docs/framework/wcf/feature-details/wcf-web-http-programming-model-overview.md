---
title: WCF Web HTTP 程式設計模型概觀
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 713dd05daa5071f253afd70e735475e49a986aa7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239012"
---
# <a name="wcf-web-http-programming-model-overview"></a>WCF Web HTTP 程式設計模型概觀

WCF) WEB HTTP 程式設計模型 Windows Communication Foundation (提供使用 WCF 建立 WEB HTTP 服務所需的基本元素。 WCF WEB HTTP 服務是設計來供最廣泛的可能用戶端（包括網頁瀏覽器）存取，並具有下列獨特需求：  
  
- **Uri 和 Uri 處理** Uri 在 WEB HTTP 服務的設計中扮演集中角色。 WCF WEB HTTP 程式設計模型使用 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable> 類別來提供 URI 處理功能。  
  
- **對 GET 和 POST 作業的支援** 除了資料修改和遠端叫用的各種調用動詞命令之外，WEB HTTP 服務還會使用 GET 動詞命令來進行資料抓取。 WCF WEB HTTP 程式設計模型使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和， <xref:System.ServiceModel.Web.WebInvokeAttribute> 將服務作業與 GET 和其他 HTTP 動詞（例如 PUT、POST 和 DELETE）產生關聯。  
  
- **多種資料格式** 除了 SOAP 訊息之外，Web 樣式服務還會處理許多種類的資料。 WCF WEB HTTP 程式設計模型使用 <xref:System.ServiceModel.WebHttpBinding> 和 <xref:System.ServiceModel.Description.WebHttpBehavior> 來支援許多不同的資料格式，包括 XML 檔、JSON 資料物件，以及二進位內容（例如影像、影片檔案或純文字）的資料流程。  
  
 WCF WEB HTTP 程式設計模型可延伸 WCF 的範圍，以涵蓋 Web 樣式案例，包括 WEB HTTP 服務、AJAX 和 JSON 服務，以及新聞訂閱 (ATOM/RSS) 摘要。 如需 AJAX 和 JSON 服務的詳細資訊，請參閱 [Ajax 整合與 Json 支援](ajax-integration-and-json-support.md)。 如需有關摘要整合的詳細資訊，請參閱 WCF 新聞訂閱 [總覽](wcf-syndication-overview.md)。  
  
 可從 WEB HTTP 服務傳回的資料型別沒有額外的限制。 WEB HTTP 服務作業可傳回任何可序列化型別。 因為 WEB HTTP 服務作業可由 Web 瀏覽器叫用，所以可在 URL 中指定的資料型別具有一項限制。 如需預設支援哪些類型的詳細資訊，請參閱下面的 **UriTemplate 查詢字串參數和 url** 一節。 您可以提供自己的 T:System.ServiceModel.Dispatcher.QueryStringConverter 實作來變更預設行為，其中指定如何將 URL 中指定的參數轉換成實際的參數型別。 如需詳細資訊，請參閱<xref:System.ServiceModel.Dispatcher.QueryStringConverter>。  
  
> [!CAUTION]
> 使用 WCF WEB HTTP 程式設計模型所撰寫的服務不會使用 SOAP 訊息。 因為不使用 SOAP，所以無法使用 WCF 提供的安全性功能。 不過，您可透過以 HTTPS 裝載服務的方式來使用傳輸型安全性。 如需 WCF 安全性的詳細資訊，請參閱 [安全性概觀](security-overview.md)  
  
> [!WARNING]
> 安裝適用於 IIS 的 WebDAV 延伸模組可能會導致 Web HTTP 服務傳回 HTTP 405 錯誤，因為 WebDAV 延伸模組會嘗試處理所有 PUT 要求。 若要解決此問題，您可以解除安裝 WebDAV 延伸模組或停用網站的 WebDAV 延伸模組。 如需詳細資訊，請參閱 [IIS 和 WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>使用 UriTemplate 和 UriTemplateTable 來進行 URI 處理  

 URI 範本提供一個有效的語法，以便表示大量結構上類似的 URI 集合。 例如，下列範本會表示以 "a" 開頭及以 "c" 結尾的所有三段式 URI 集合 (不論是否有中繼區段：a/{segment}/c)。  
  
 此範本會說明類似下列的 URI：  
  
- a/x/c  
  
- a/y/c  
  
- a/z/c  
  
- 依此類推。  
  
 在此範本中，大括號標記法 ("{segment}") 表示變數區段，而不是常值。  
  
 .NET Framework 提供可以使用 <xref:System.UriTemplate> 這種 URI 範本的應用程式開發介面。 `UriTemplates` 可讓您執行下列作業：  
  
- 您可以 `Bind` 使用一組參數來呼叫其中一個方法，以產生符合範本的 *完整關閉 URI* 。 意思就是，URI 範本中的所有變數都會以實際值來取代。  
  
- 您可以使用候選 URI 來呼叫 `Match`()，以便透過範本將候選 URI 切割為自身的構成部分，並傳回包含不同的 URI (已依據範本中的變數加上標籤) 部分的字典。  
  
- `Bind`() 和 `Match`() 都是反向值，因此您可以呼叫 `Match`( `Bind`( x ) ) 並從一開始的相同環境重新開始。  
  
 在許多情況下 (特別是在伺服器上，需要根據 URI 將要求分派到服務作業時) 您都想要追蹤資料結構中可以獨立處理每一個包含的範本的 <xref:System.UriTemplate> 物件集合。 <xref:System.UriTemplateTable> 表示一組 URI 範本，並且依據一組指定的範本及候選 URI 選取最佳對象。 這不會與任何特定的網路堆疊關聯 (WCF 包含) 因此您可以在必要時使用它。  
  
 WCF 服務模型會透過 <xref:System.UriTemplate> 和 <xref:System.UriTemplateTable> 將服務作業與 <xref:System.UriTemplate> 所描述的 URI 集合關聯在一起。 服務作業會透過 <xref:System.UriTemplate> 或 <xref:System.ServiceModel.Web.WebGetAttribute>，與 <xref:System.ServiceModel.Web.WebInvokeAttribute> 產生關聯。 如需和的詳細資訊 <xref:System.UriTemplate> <xref:System.UriTemplateTable> ，請參閱 [UriTemplate 和 UriTemplateTable](uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet 和 WebInvoke 屬性  

 WCF WEB HTTP 服務會使用抓取動詞 (例如 HTTP GET) ，以及各種調用動詞 (例如 HTTP POST、PUT 和 DELETE) 。 WCF WEB HTTP 程式設計模型可讓服務開發人員使用和來控制與其服務作業相關聯的 URI 範本和動詞 <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> 。 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 可讓您控制個別作業如何繫結至 URI 及與這些 URI 相關聯的 HTTP 方法。 例如，在下列程式碼中新增 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute>。  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 先前的程式碼可讓您進行下列 HTTP 要求。  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> 會預設為 POST，但是您還是可以用它來控制其他動詞。  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 若要查看使用 WCF WEB HTTP 程式設計模型之 WCF 服務的完整範例，請參閱 how [to：建立基本 Wcf WEB Http 服務](how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>UriTemplate 查詢字串參數和 URL  

 您可以輸入與服務作業關聯的 URL，透過網頁瀏覽器呼叫 Web 樣式服務。 這些服務作業可接受的查詢字串參數，必須在 URL 中以字串格式指定。 下表說明可由 URL 傳遞的型別及採用的格式。  
  
|類型|格式|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (不需要指數標記法)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (不需要指數標記法)|  
|<xref:System.Char>|任何單一字元|  
|<xref:System.Decimal>|標準標記法中任何一個小數 (不含指數)|  
|<xref:System.Boolean>|True 或 False (不區分大小寫)|  
|<xref:System.String>|任何字串 (不支援 null 字串且不會進行逸出)|  
|<xref:System.DateTime>|MM/DD/YYYY<br /><br /> MM/DD/YYYY HH： MM： SS [AM&#124;PM]<br /><br /> 月/日/年<br /><br /> Month Day Year HH： MM： SS [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> 其中 DD = 天數，HH = 小時，MM = 分鐘，SS = 秒數|  
|<xref:System.Guid>|GUID，例如：<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> 其中 DD = 天數，HH = 小時，MM = 分鐘，SS = 秒數|  
|列舉|列舉值，依下列程式碼示範的方式定義列舉。<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> 任何個別的列舉值 (或其對應的整數值) 都可以在查詢字串中指定。|  
|具有可以在型別和字串表示之間相互轉換之 `TypeConverterAttribute` 的型別。|取決於型別轉換子。|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>格式與 WCF WEB HTTP 程式設計模型  

 WCF WEB HTTP 程式設計模型有新的功能，可使用許多不同的資料格式。 在繫結層，<xref:System.ServiceModel.WebHttpBinding> 可以讀取並寫入下列不同種類的資料：  
  
- XML  
  
- JSON  
  
- 不透明的二進位資料流  
  
 這表示 WCF WEB HTTP 程式設計模型可以處理任何類型的資料，但您可能會進行程式設計 <xref:System.IO.Stream> 。  
  
 .NET Framework 3.5 提供 JSON 資料的支援 (AJAX) 以及新聞訂閱摘要 (包括 ATOM 和 RSS) 。 如需這些功能的詳細資訊，請參閱 [Wcf WEB HTTP 格式](wcf-web-http-formatting.md)、 [Wcf 摘要整合總覽](wcf-syndication-overview.md)，以及 [AJAX 整合和 JSON 支援](ajax-integration-and-json-support.md)。  
  
## <a name="wcf-web-http-programming-model-and-security"></a>WCF WEB HTTP 程式設計模型和安全性  

因為 WCF WEB HTTP 程式設計模型不支援 WS-* 通訊協定，保護 WCF WEB HTTP 服務的唯一方法是使用 SSL 透過 HTTPS 公開服務。 如需使用 IIS 7.0 設定 SSL 的詳細資訊，請參閱 [如何在 iis 中執行 ssl](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis)。
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>WCF WEB HTTP 程式設計模型疑難排解  

 當呼叫 WCF WEB HTTP 服務以使用 <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> 建立通道時，<xref:System.ServiceModel.Description.WebHttpBehavior> 會使用組態檔中設定的 <xref:System.ServiceModel.EndpointAddress>，即便傳遞至 <xref:System.ServiceModel.EndpointAddress> 的 <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> 是另一個值亦然。  
  
## <a name="see-also"></a>另請參閱

- [WCF 新聞訂閱](wcf-syndication.md)
- [WCF Web HTTP 程式設計物件模型](wcf-web-http-programming-object-model.md)
- [WCF Web HTTP 程式設計模型](wcf-web-http-programming-model.md)

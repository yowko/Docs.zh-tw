---
title: 獨立診斷摘要範例
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 29d8caee48925040db9f1812f015870e3a1272bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144002"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>獨立診斷摘要範例
此示例演示如何創建 RSS/原子源，以便與 Windows 通信基礎 （WCF） 聯合使用。 它是一個基本的"Hello World"程式，它顯示了物件模型的基礎知識以及如何在 Windows 通信基礎 （WCF） 服務上設置它。  
  
 WCF 將聯合饋送建模為返回特殊資料類型的服務操作<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>。 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的執行個體可將摘要序列化至 RSS 2.0 和 Atom 1.0 格式。 下列範例程式碼會顯示使用的合約。  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 該`GetProcesses`操作使用<xref:System.ServiceModel.Web.WebGetAttribute>屬性進行批號，該屬性使您能夠控制 WCF 如何向服務操作發送 HTTP GET 請求並指定所發送消息的格式。  
  
 與任何 WCF 服務一樣，聯合饋送可以在任何託管應用程式中自行託管。 新聞訂閱服務需要指定的繫結 (<xref:System.ServiceModel.WebHttpBinding>) 和指定的端點行為 (<xref:System.ServiceModel.Description.WebHttpBehavior>) 才能正常運作。 新的 <xref:System.ServiceModel.Web.WebServiceHost> 類別提供方便的 API，不需特定的組態即可建立這類端點。  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 或者，您可以使用 IIS 裝載 .svc 檔案內的 <xref:System.ServiceModel.Activation.WebServiceHostFactory>，提供等同的功能 (本範例程式碼中未示範這項技術)。  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 因為這個服務使用標準 HTTP GET 接收要求，所以您可以使用任何 RSS 或 ATOM 感知用戶端來存取服務。 例如，您可以通過導航到`http://localhost:8000/diagnostics/feed/?format=atom`RSS 感知瀏覽器或在`http://localhost:8000/diagnostics/feed/?format=rss`RSS 感知瀏覽器中查看此服務的輸出。
  
 您還可以使用[WCF 聯合物件模型如何映射到 Atom 和 RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)來讀取聯合資料並使用命令代碼處理資料。  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a>設置、生成和運行示例
  
1. 確保電腦上具有 HTTP 和 HTTPS 的正確位址註冊許可權，如[Windows 通信基礎示例的一次性設置過程](one-time-setup-procedure-for-the-wcf-samples.md)中的設置說明中所述。

2. 建置方案。

3. 執行主控台應用程式。

4. 在主控台應用程式運行時，導航到`http://localhost:8000/diagnostics/feed/?format=atom`或使用`http://localhost:8000/diagnostics/feed/?format=rss`RSS 感知瀏覽器。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a>另請參閱

- [WCF Web HTTP 程式設計模型](../feature-details/wcf-web-http-programming-model.md)
- [WCF 新聞訂閱](../feature-details/wcf-syndication.md)

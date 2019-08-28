---
title: 獨立診斷摘要範例
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 6b83bda154a76fe10487da00359e0ceace8ce8cb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044672"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>獨立診斷摘要範例
這個範例會示範如何使用 Windows Communication Foundation (WCF) 來建立新聞訂閱的 RSS/Atom 摘要。 這是一個基本的「Hello World」程式, 會顯示物件模型的基本概念, 以及如何在 Windows Communication Foundation (WCF) 服務上進行設定。  
  
 WCF 會將新聞訂閱摘要當做傳回特殊資料類型<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>的服務作業來模型。 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的執行個體可將摘要序列化至 RSS 2.0 和 Atom 1.0 格式。 下列範例程式碼會顯示使用的合約。  
  
```  
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
  
 `GetProcesses`作業是<xref:System.ServiceModel.Web.WebGetAttribute>以屬性標注, 可讓您控制 WCF 將 HTTP GET 要求分派至服務作業的方式, 以及指定所傳送訊息的格式。  
  
 就像任何 WCF 服務一樣, 新聞訂閱摘要可以自我裝載于任何受控應用程式中。 新聞訂閱服務需要指定的繫結 (<xref:System.ServiceModel.WebHttpBinding>) 和指定的端點行為 (<xref:System.ServiceModel.Description.WebHttpBehavior>) 才能正常運作。 新的 <xref:System.ServiceModel.Web.WebServiceHost> 類別提供方便的 API，不需特定的組態即可建立這類端點。  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 或者，您可以使用 IIS 裝載 .svc 檔案內的 <xref:System.ServiceModel.Activation.WebServiceHostFactory>，提供等同的功能 (本範例程式碼中未示範這項技術)。  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 因為這個服務使用標準 HTTP GET 接收要求，所以您可以使用任何 RSS 或 ATOM 感知用戶端來存取服務。 例如, 您可以流覽至`http://localhost:8000/diagnostics/feed/?format=atom`或`http://localhost:8000/diagnostics/feed/?format=rss` RSS 感知瀏覽器, 以查看此服務的輸出。
  
 您也可以使用 WCF 新聞訂閱[物件模型對應到 Atom 和 RSS 的方式](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)來讀取同步發行的資料, 並使用命令式程式碼處理它。  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您擁有電腦上 HTTP 和 HTTPS 的正確位址註冊許可權, 如[Windows Communication Foundation 範例的一次性設定程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)中所述。  
  
2. 建置方案。  
  
3. 執行主控台應用程式 (Console Application)。  
  
4. 執行主控台應用程式時，瀏覽至 `http://localhost:8000/diagnostics/feed/?format=atom` 或 `http://localhost:8000/diagnostics/feed/?format=rss` 使用 RSS 感知瀏覽器。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>另請參閱

- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF 摘要整合](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)

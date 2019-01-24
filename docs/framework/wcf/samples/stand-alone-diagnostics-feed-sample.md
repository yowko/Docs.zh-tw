---
title: 獨立診斷摘要範例
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 53eadcb8ad806fdec60739c8422abe05087cb937
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707683"
---
# <a name="stand-alone-diagnostics-feed-sample"></a>獨立診斷摘要範例
此範例示範如何建立 RSS/Atom 摘要的新聞訂閱與 Windows Communication Foundation (WCF)。 它會顯示物件模型的基本概念以及如何設定 Windows Communication Foundation (WCF) 服務上的基本"Hello World"程式。  
  
 WCF 新聞訂閱摘要製作為服務作業傳回特殊資料型別的<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>。 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 的執行個體可將摘要序列化至 RSS 2.0 和 Atom 1.0 格式。 下列範例程式碼會顯示使用的合約。  
  
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
  
 `GetProcesses`作業註解<xref:System.ServiceModel.Web.WebGetAttribute>屬性，可讓您控制 WCF 分派 HTTP GET 要求至服務作業，並指定傳送的訊息格式。  
  
 如同任何 WCF 服務，新聞訂閱摘要，也可以是自我裝載於任何 managed 應用程式。 新聞訂閱服務需要指定的繫結 (<xref:System.ServiceModel.WebHttpBinding>) 和指定的端點行為 (<xref:System.ServiceModel.Description.WebHttpBehavior>) 才能正常運作。 新的 <xref:System.ServiceModel.Web.WebServiceHost> 類別提供方便的 API，不需特定的組態即可建立這類端點。  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 或者，您可以使用 IIS 裝載 .svc 檔案內的 <xref:System.ServiceModel.Activation.WebServiceHostFactory>，提供等同的功能 (本範例程式碼中未示範這項技術)。  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 因為這個服務使用標準 HTTP GET 接收要求，所以您可以使用任何 RSS 或 ATOM 感知用戶端來存取服務。 比方說，您可以檢視此服務的輸出，瀏覽至`http://localhost:8000/diagnostics/feed/?format=atom`或`http://localhost:8000/diagnostics/feed/?format=rss`RSS 感知瀏覽器中。
  
 您也可以使用[如何 WCF 新聞訂閱物件模型對應到 Atom 和 RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)讀取新聞訂閱方式的資料，並使用命令式程式碼進行處理。  
  
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
  
1.  請確定您已正確位址註冊權限 HTTP 與 HTTPS 在電腦上的，安裝指示中所述[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  建置方案。  
  
3.  執行主控台應用程式 (Console Application)。  
  
4.  執行主控台應用程式時，瀏覽至 `http://localhost:8000/diagnostics/feed/?format=atom` 或 `http://localhost:8000/diagnostics/feed/?format=rss` 使用 RSS 感知瀏覽器。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>另請參閱
- [WCF Web HTTP 程式設計模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF 摘要整合](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)

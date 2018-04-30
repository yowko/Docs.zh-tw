---
title: 資料流摘要範例
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1eb5d8e0b19bc32ea5158d1614447b76f4924440
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="2f86c-102">資料流摘要範例</span><span class="sxs-lookup"><span data-stu-id="2f86c-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="2f86c-103">這個範例會示範如何管理含有大量項目的新聞訂閱摘要。</span><span class="sxs-lookup"><span data-stu-id="2f86c-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="2f86c-104">在伺服器上，此範例會示範如何在項目即將寫入網路資料流的之前立即延遲建立摘要中個別的 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件。</span><span class="sxs-lookup"><span data-stu-id="2f86c-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="2f86c-105">在用戶端上，此範例將示範如何使用自訂新聞訂閱摘要格式器從網路資料流讀取個別項目，讓讀取的摘要絕對不會完全在緩衝記憶體中。</span><span class="sxs-lookup"><span data-stu-id="2f86c-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="2f86c-106">為了充分示範新聞訂閱 API 的資料流處理能力，在這個範例中，伺服器會公開包含無限數目項目的摘要 (這種情況不太可能發生)。</span><span class="sxs-lookup"><span data-stu-id="2f86c-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="2f86c-107">在這個情況中，伺服器會持續在摘要中產生新的項目，直到摘要判斷用戶端已經從摘要讀取了指定數目的項目 (預設為 10)。</span><span class="sxs-lookup"><span data-stu-id="2f86c-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="2f86c-108">為了簡要說明，我們在同一個處理序中同時實作用戶端和伺服器，並使用共用的 `ItemCounter` 物件來追蹤用戶端已經產生了多少數目的項目。</span><span class="sxs-lookup"><span data-stu-id="2f86c-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="2f86c-109">`ItemCounter` 型別存在的唯一理由，就是讓範例案例正常地終止，但此型別不是我們要示範的核心模式項目。</span><span class="sxs-lookup"><span data-stu-id="2f86c-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="2f86c-110">示範會使用 Visual C# 的迭代器 (使用`yield``return`關鍵字建構)。</span><span class="sxs-lookup"><span data-stu-id="2f86c-110">The demonstration makes use of Visual C# iterators (using the `yield``return` keyword construct).</span></span> <span data-ttu-id="2f86c-111">如需迭代器的詳細資訊，請參閱 MSDN 上的 < 使用 Iterator > 主題。</span><span class="sxs-lookup"><span data-stu-id="2f86c-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="2f86c-112">服務</span><span class="sxs-lookup"><span data-stu-id="2f86c-112">Service</span></span>  
 <span data-ttu-id="2f86c-113">此服務會實作由一個作業組成的基本 <xref:System.ServiceModel.Web.WebGetAttribute> 合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2f86c-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="2f86c-114">此服務會透過 `ItemGenerator` 類別並使用 Iterator 來建立可能無限的 <xref:System.ServiceModel.Syndication.SyndicationItem> 執行個體資料流，以實作此合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2f86c-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```  
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="2f86c-115">當服務實作建立摘要時，就會使用 `ItemGenerator.GenerateItems()` 的輸出，而非經過緩衝處理的項目集合。</span><span class="sxs-lookup"><span data-stu-id="2f86c-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```  
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="2f86c-116">這樣一來，項目資料流就永遠不會經過記憶體緩衝處理了。</span><span class="sxs-lookup"><span data-stu-id="2f86c-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="2f86c-117">您可以觀察此行為上設定中斷點`yield``return`陳述式內的`ItemGenerator.GenerateItems()`方法，您會看到，服務傳回的結果之後，首次遇到此中斷點`StreamedFeed()`方法。</span><span class="sxs-lookup"><span data-stu-id="2f86c-117">You can observe this behavior by setting a breakpoint on the `yield``return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="2f86c-118">用戶端</span><span class="sxs-lookup"><span data-stu-id="2f86c-118">Client</span></span>  
 <span data-ttu-id="2f86c-119">這個範例中的用戶端會使用自訂 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 實作，這個實作會延遲具體化摘要中的個別項目，而不是經過記憶體來緩衝處理它們。</span><span class="sxs-lookup"><span data-stu-id="2f86c-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="2f86c-120">下列為自訂 `StreamedAtom10FeedFormatter` 執行個體的使用方式。</span><span class="sxs-lookup"><span data-stu-id="2f86c-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="2f86c-121">一般來說，除非已經從網路讀取完整的摘要內容，並經過記憶體緩衝處理，否則不會傳回對 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2f86c-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="2f86c-122">不過，`StreamedAtom10FeedFormatter` 物件會覆寫 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> 以傳回 Iterator (而不是緩衝處理的集合)，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2f86c-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="2f86c-123">這樣一來，除非周遊 `ReadItems()` 結果的用戶端應用程式準備好要使用每個項目，否則無法從網路讀取每個項目。</span><span class="sxs-lookup"><span data-stu-id="2f86c-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="2f86c-124">您可以觀察此行為上設定中斷點`yield``return`陳述式內的`StreamedAtom10FeedFormatter.DelayReadItems()`並注意，在呼叫之後第一次遇到此中斷點`ReadFrom()`完成。</span><span class="sxs-lookup"><span data-stu-id="2f86c-124">You can observe this behavior by setting a breakpoint on the `yield``return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="2f86c-125">下列指示說明如何建置並執行範例。</span><span class="sxs-lookup"><span data-stu-id="2f86c-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="2f86c-126">請注意，雖然伺服器會在用戶端讀取 10 次之後已經停止產生項目，但輸出仍會顯示用戶端明顯讀取了 10 次以上。</span><span class="sxs-lookup"><span data-stu-id="2f86c-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="2f86c-127">這是因為範例所使用的網路繫結會以 4 KB 的區段為一個單位來傳送資料。</span><span class="sxs-lookup"><span data-stu-id="2f86c-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="2f86c-128">因此，用戶端根本沒機會讀取項目，就會立即收到 4 KB 大小的項目資料。</span><span class="sxs-lookup"><span data-stu-id="2f86c-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="2f86c-129">這是正常行為 (透過合理大小的區段來傳送資料流處理的 HTTP 資料能夠提升效能)。</span><span class="sxs-lookup"><span data-stu-id="2f86c-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2f86c-130">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="2f86c-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2f86c-131">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2f86c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2f86c-132">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="2f86c-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2f86c-133">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="2f86c-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2f86c-134">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="2f86c-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2f86c-135">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="2f86c-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2f86c-136">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="2f86c-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2f86c-137">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="2f86c-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="2f86c-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f86c-138">See Also</span></span>  
 [<span data-ttu-id="2f86c-139">獨立診斷摘要</span><span class="sxs-lookup"><span data-stu-id="2f86c-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)

---
title: 資料流摘要範例
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 735a72cba3c953ea4774d89751dad3216aa44400
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257180"
---
# <a name="streaming-feeds-sample"></a>資料流摘要範例

這個範例會示範如何管理含有大量項目的新聞訂閱摘要。 在伺服器上，此範例會示範如何在項目即將寫入網路資料流的之前立即延遲建立摘要中個別的 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件。  
  
 在用戶端上，此範例將示範如何使用自訂新聞訂閱摘要格式器從網路資料流讀取個別項目，讓讀取的摘要絕對不會完全在緩衝記憶體中。  
  
 為了充分示範新聞訂閱 API 的資料流處理能力，在這個範例中，伺服器會公開包含無限數目項目的摘要 (這種情況不太可能發生)。 在這個情況中，伺服器會持續在摘要中產生新的項目，直到摘要判斷用戶端已經從摘要讀取了指定數目的項目 (預設為 10)。 為了簡要說明，我們在同一個處理序中同時實作用戶端和伺服器，並使用共用的 `ItemCounter` 物件來追蹤用戶端已經產生了多少數目的項目。 `ItemCounter` 型別存在的唯一理由，就是讓範例案例正常地終止，但此型別不是我們要示範的核心模式項目。  
  
 示範會使用 Visual c # 反覆運算器 (使用 `yield return` 關鍵字結構) 。 如需有關反覆運算器的詳細資訊，請參閱 MSDN 上的「使用反覆運算器」主題。  
  
## <a name="service"></a>服務  

 此服務會實作由一個作業組成的基本 <xref:System.ServiceModel.Web.WebGetAttribute> 合約，如下列程式碼所示。  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 此服務會透過 `ItemGenerator` 類別並使用 Iterator 來建立可能無限的 <xref:System.ServiceModel.Syndication.SyndicationItem> 執行個體資料流，以實作此合約，如下列程式碼所示。  
  
```csharp
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
  
 當服務實作建立摘要時，就會使用 `ItemGenerator.GenerateItems()` 的輸出，而非經過緩衝處理的項目集合。  
  
```csharp
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
  
 這樣一來，項目資料流就永遠不會經過記憶體緩衝處理了。 您可以藉由在方法內的語句上設定中斷點來觀察這項行為 `yield return` `ItemGenerator.GenerateItems()` ，並注意在服務傳回方法的結果之後，第一次遇到這個中斷點 `StreamedFeed()` 。  
  
## <a name="client"></a>用戶端  

 這個範例中的用戶端會使用自訂 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 實作，這個實作會延遲具體化摘要中的個別項目，而不是經過記憶體來緩衝處理它們。 下列為自訂 `StreamedAtom10FeedFormatter` 執行個體的使用方式。  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 一般來說，除非已經從網路讀取完整的摘要內容，並經過記憶體緩衝處理，否則不會傳回對 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> 的呼叫。 不過，`StreamedAtom10FeedFormatter` 物件會覆寫 <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> 以傳回 Iterator (而不是緩衝處理的集合)，如下列程式碼所示。  
  
```csharp  
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
  
 這樣一來，除非周遊 `ReadItems()` 結果的用戶端應用程式準備好要使用每個項目，否則無法從網路讀取每個項目。 您可以藉由在的語句中設定中斷點來觀察這項行為 `yield return` `StreamedAtom10FeedFormatter.DelayReadItems()` ，並注意到在呼叫完成之後第一次遇到這個中斷點 `ReadFrom()` 。  
  
 下列指示說明如何建置並執行範例。 請注意，雖然伺服器會在用戶端讀取 10 次之後已經停止產生項目，但輸出仍會顯示用戶端明顯讀取了 10 次以上。 這是因為範例所使用的網路繫結會以 4 KB 的區段為一個單位來傳送資料。 因此，用戶端根本沒機會讀取項目，就會立即收到 4 KB 大小的項目資料。 這是正常行為 (透過合理大小的區段來傳送資料流處理的 HTTP 資料能夠提升效能)。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確定您已 [針對 Windows Communication Foundation 範例執行一次性安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦的設定中執行範例，請遵循執行 [Windows Communication Foundation 範例](running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>另請參閱

- [獨立診斷摘要](stand-alone-diagnostics-feed-sample.md)

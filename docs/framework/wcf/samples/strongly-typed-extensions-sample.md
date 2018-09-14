---
title: 強型別延伸範例
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: eccb0ce240d01ab8592a44daddcfa7aa3d2023fb
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45568410"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="5856a-102">強型別延伸範例</span><span class="sxs-lookup"><span data-stu-id="5856a-102">Strongly-Typed Extensions Sample</span></span>
<span data-ttu-id="5856a-103">基於示範用途，此範例會使用 <xref:System.ServiceModel.Syndication.SyndicationFeed> 類別。</span><span class="sxs-lookup"><span data-stu-id="5856a-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="5856a-104">不過在此範例中所示範的模式，可以與所有支援延伸資料的新聞訂閱類別一起使用。</span><span class="sxs-lookup"><span data-stu-id="5856a-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="5856a-105">Syndication 物件模型 (<xref:System.ServiceModel.Syndication.SyndicationFeed>、<xref:System.ServiceModel.Syndication.SyndicationItem> 和相關類別) 會使用 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 和 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 屬性，藉此支援對延伸資料的鬆散型別存取。</span><span class="sxs-lookup"><span data-stu-id="5856a-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="5856a-106">此範例說明如何實作 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 的自訂衍生型別，以便使用某些特定應用程式延伸資料做為強型別屬性，藉此提供對延伸資料的強型別存取。</span><span class="sxs-lookup"><span data-stu-id="5856a-106">This sample shows how to provide strongly-typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly-typed properties.</span></span>  
  
 <span data-ttu-id="5856a-107">例如，此範例說明如何實作在建議的 Atom Threading Extensions RFC 中定義的延伸項目。</span><span class="sxs-lookup"><span data-stu-id="5856a-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="5856a-108">這僅做為示範之用，不適合直接用於建議規格的完整實作中。</span><span class="sxs-lookup"><span data-stu-id="5856a-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="5856a-109">範例 XML</span><span class="sxs-lookup"><span data-stu-id="5856a-109">Sample XML</span></span>  
 <span data-ttu-id="5856a-110">下列 XML 範例顯示具有其他 `<in-reply-to>` 延伸項目的 Atom 1.0 項目。</span><span class="sxs-lookup"><span data-stu-id="5856a-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"   
                 p3:href="http://www.example.org/entries/1"   
                 p3:type="application/xhtml+xml"   
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"   
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="5856a-111">`<in-reply-to>`項目會指定三個必要的屬性 (`ref`，`type`和`href`) 同時又能讓其他擴充屬性和延伸模組項目是否存在。</span><span class="sxs-lookup"><span data-stu-id="5856a-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="5856a-112">建立 In-Reply-To 項目的模型</span><span class="sxs-lookup"><span data-stu-id="5856a-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="5856a-113">在本範例中，`<in-reply-to>` 項目會模型化為實作 <xref:System.Xml.Serialization.IXmlSerializable> 以便與 <xref:System.Runtime.Serialization.DataContractSerializer> 搭配使用的 CLR。</span><span class="sxs-lookup"><span data-stu-id="5856a-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="5856a-114">此外，它也會實作用於存取項目資料的方法和屬性，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5856a-114">It also implements some methods and properties for accessing the element’s data, as shown in the following sample code.</span></span>  
  
```  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =   
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,   
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="5856a-115">`InReplyToElement` 類別會針對必要的屬性 (Attribute) (`HRef`、`MediaType` 和 `Source`) 以及集合實作屬性 (Property)，以保存 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 和 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>。</span><span class="sxs-lookup"><span data-stu-id="5856a-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="5856a-116">`InReplyToElement` 類別會實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面，這個介面允許直接控制要以何種方式從 XML 讀取物件執行個體，以及將物件執行個體寫入至 XML。</span><span class="sxs-lookup"><span data-stu-id="5856a-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="5856a-117">`ReadXml` 方法會先從傳遞給它的 `Ref` 讀取 `HRef`、`Source`、`MediaType` 以及 <xref:System.Xml.XmlReader> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5856a-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="5856a-118">任何未知的屬性都會儲存在 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="5856a-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="5856a-119">當讀取過所有屬性之後，就會呼叫 <xref:System.Xml.XmlReader.ReadStartElement> 使讀取器前進至下一個項目。</span><span class="sxs-lookup"><span data-stu-id="5856a-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="5856a-120">由於此類別建立模型的項目沒有所需的子系，因此子項目會緩衝處理至 `XElement` 執行個體並儲存在 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 集合中，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5856a-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```  
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new   
                                 XmlQualifiedName(reader.LocalName,   
                                 reader.NamespaceURI),   
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="5856a-121">在 `WriteXml` 中，`InReplyToElement` 方法會先寫出 `Ref`、`HRef`、`Source` 和 `MediaType` 屬性 (Property) 的值做為 XML 屬性 (Attribute) (`WriteXml` 不負責自己寫入實際外部項目，因為這項作業是由 `WriteXml` 的呼叫者來完成)。</span><span class="sxs-lookup"><span data-stu-id="5856a-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="5856a-122">此外，它也會將 <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> 和 <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> 的內容寫入至寫入器，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5856a-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```  
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,   
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,   
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,   
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,   
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in   
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,   
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="5856a-123">ThreadedFeed 和 ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="5856a-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="5856a-124">在此範例中，具有 `SyndicationItems` 延伸的 `InReplyTo` 是由 `ThreadedItem` 類別模型化。</span><span class="sxs-lookup"><span data-stu-id="5856a-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="5856a-125">同樣地，`ThreadedFeed` 類別是 `SyndicationFeed`，其項目都是 `ThreadedItem` 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5856a-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="5856a-126">`ThreadedFeed` 類別繼承自 `SyndicationFeed`，並且會覆寫 `OnCreateItem` 以傳回 `ThreadedItem`。</span><span class="sxs-lookup"><span data-stu-id="5856a-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="5856a-127">它也實作用來存取 `Items` 集合做為 `ThreadedItems` 的方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5856a-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```  
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="5856a-128">類別 `ThreadedItem` 繼承自 `SyndicationItem`，並且會使 `InReplyToElement` 成為強型別屬性。</span><span class="sxs-lookup"><span data-stu-id="5856a-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly-typed property.</span></span> <span data-ttu-id="5856a-129">這可提供方便、程式設計的方式來存取 `InReplyTo` 延伸資料。</span><span class="sxs-lookup"><span data-stu-id="5856a-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="5856a-130">它也會實作 `TryParseElement` 和 `WriteElementExtensions` 以便讀取和寫入其延伸資料，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="5856a-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```  
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,   
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,   
                                                 string version)  
    {  
        if (this.InReplyTo != null &&   
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,   
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5856a-131">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5856a-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5856a-132">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5856a-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5856a-133">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="5856a-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5856a-134">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="5856a-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5856a-135">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5856a-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5856a-136">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5856a-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5856a-137">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="5856a-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5856a-138">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5856a-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="5856a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5856a-139">See Also</span></span>

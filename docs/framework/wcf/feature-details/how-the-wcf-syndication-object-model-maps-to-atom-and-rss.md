---
title: "WCF 新聞訂閱物件模型對應到 Atom 和 RSS 的方式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01030ed226a5cdc384db56933325d7c4eeade989
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a><span data-ttu-id="f424e-102">WCF 新聞訂閱物件模型對應到 Atom 和 RSS 的方式</span><span class="sxs-lookup"><span data-stu-id="f424e-102">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>
<span data-ttu-id="f424e-103">在您開發 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 新聞訂閱服務時，會使用下列類別來建立摘要與項目：</span><span class="sxs-lookup"><span data-stu-id="f424e-103">When developing a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] syndication service, you create feeds and items using the following classes:</span></span>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <span data-ttu-id="f424e-104"><xref:System.ServiceModel.Syndication.SyndicationFeed> 可以序列化為任何一種用來定義格式器的同步發佈格式。</span><span class="sxs-lookup"><span data-stu-id="f424e-104">A <xref:System.ServiceModel.Syndication.SyndicationFeed> can be serialized into any syndication format for which a formatter is defined.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f424e-105"> 會隨附兩個格式器：<xref:System.ServiceModel.Syndication.Atom10FeedFormatter> 和 <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>。</span><span class="sxs-lookup"><span data-stu-id="f424e-105"> ships with two formatters: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> and <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.</span></span>  
  
 <span data-ttu-id="f424e-106">在 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 周圍的物件模型會與 Atom 1.0 規格 (而不是 RSS 2.0 規格) 較為符合。</span><span class="sxs-lookup"><span data-stu-id="f424e-106">The object model around <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> is aligned more closely with the Atom 1.0 specification than the RSS 2.0 specification.</span></span> <span data-ttu-id="f424e-107">這是因為 Atom 1.0 是比較實質上的規格，可用來定義不明確或是從 RSS 2.0 規格中省略的項目。</span><span class="sxs-lookup"><span data-stu-id="f424e-107">This is because Atom 1.0 is a more substantial specification that defines elements that are ambiguous or omitted from the RSS 2.0 specification.</span></span> <span data-ttu-id="f424e-108">由於這個原因，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 新聞訂閱物件模型中的許多項目並未在 RSS 2.0 規格中具有直接代表項。</span><span class="sxs-lookup"><span data-stu-id="f424e-108">Because of this, many items in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syndication object model have no direct representation in the RSS 2.0 specification.</span></span> <span data-ttu-id="f424e-109">當您將 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 物件序列化為 RSS 2.0 時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可讓您將 Atom 特定的資料項目序列化為符合命名空間延伸項目以符合 Atom 規格。</span><span class="sxs-lookup"><span data-stu-id="f424e-109">When serializing <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> objects into RSS 2.0, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you to serialize Atom-specific data elements as namespace-qualified extension elements that conform to the Atom specification.</span></span> <span data-ttu-id="f424e-110">您可以將參數傳遞至 <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> 建構函式來控制這個項目。</span><span class="sxs-lookup"><span data-stu-id="f424e-110">You can control this with a parameter passed to the <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> constructor.</span></span>  
  
 <span data-ttu-id="f424e-111">本主題中的程式碼範例將使用此處所定義的兩種方法之一來實際執行序列化作業。</span><span class="sxs-lookup"><span data-stu-id="f424e-111">The code samples in this topic use one of two methods defined here to do the actual serialization.</span></span>  
  
 <span data-ttu-id="f424e-112">`SerializeFeed` 會序列化新聞訂閱摘要。</span><span class="sxs-lookup"><span data-stu-id="f424e-112">`SerializeFeed` serializes a syndication feed.</span></span>  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 <span data-ttu-id="f424e-113">`SerializeItem` 會序列化新聞訂閱項目。</span><span class="sxs-lookup"><span data-stu-id="f424e-113">`SerializeItem` serializes a syndication item.</span></span>  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a><span data-ttu-id="f424e-114">SyndicationFeed</span><span class="sxs-lookup"><span data-stu-id="f424e-114">SyndicationFeed</span></span>  
 <span data-ttu-id="f424e-115">下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationFeed> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-115">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationFeed> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 <span data-ttu-id="f424e-116">下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationFeed> 如何序列化為 Atom 1.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-116">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to Atom 1.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<feed xml:lang="EN-US" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text">My Feed Title</title>  
  <subtitle type="text">My Feed Description</subtitle>  
  <id>FeedID</id>  
  <rights type="text">Copyright 2007</rights>  
  <updated>2007-08-29T13:57:17-07:00</updated>  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <logo>http://server/image.jpg</logo>  
  <generator>Sample Code</generator>  
  <link rel="alternate" href="http://myfeeduri/" />  
  <entry>  
    <id>ItemID</id>  
    <title type="text">Item Title</title>  
    <summary type="text">Item Summary</summary>  
    <published>2007-08-29T00:00:00-07:00</published>  
    <updated>2007-08-29T13:57:17-07:00</updated>  
    <author>  
      <name>Jesper Aaberg</name>  
      <uri>http://Jesper/Aaberg</uri>  
      <email>Jesper@Aaberg.com</email>  
    </author>  
    <contributor>  
      <name>Lene Aaling</name>  
      <uri>http://Lene/Aaling</uri>  
      <email>Lene@Aaling.com</email>  
    </contributor>  
    <link rel="alternate" href="http://myitemuri/" />  
    <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
    <content type="text">Item Content</content>  
    <rights type="text">Copyright 2007</rights>  
    <source>  
      <title type="text">My Feed Title</title>  
      <subtitle type="text">My Feed Description</subtitle>  
      <id>FeedID</id>  
      <rights type="text">Copyright 2007</rights>  
      <updated>2007-08-29T13:57:17-07:00</updated>  
      <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
      <logo>http://server/image.jpg</logo>  
      <generator>Sample Code</generator>  
      <link rel="alternate" href="http://myfeeduri/" />  
    </source>  
  </entry>  
</feed>  
```  
  
 <span data-ttu-id="f424e-117">下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationFeed> 將如何序列化為 RSS 2.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-117">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationFeed> is serialized to RSS 2.0.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<rss xmlns:a10="http://www.w3.org/2005/Atom" version="2.0">  
  <channel>  
    <title>My Feed Title</title>  
    <link>http://myfeeduri/</link>  
    <description>My Feed Description</description>  
    <language>EN-US</language>  
    <copyright>Copyright 2007</copyright>  
    <lastBuildDate>Wed, 29 Aug 2007 13:57:17 -0700</lastBuildDate>  
    <category domain="categoryScheme">categoryName</category>  
    <generator>Sample Code</generator>  
    <image>  
      <url>http://server/image.jpg</url>  
      <title>My Feed Title</title>  
      <link>http://myfeeduri/</link>  
    </image>  
    <a10:id>FeedID</a10:id>  
    <item>  
      <guid isPermaLink="false">ItemID</guid>  
      <link>http://myitemuri/</link>  
      <author>Jesper@Aaberg.com</author>  
      <category domain="categoryScheme">categoryName</category>  
      <title>Item Title</title>  
      <description>Item Summary</description>  
      <source>My Feed Title</source>  
      <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
      <a10:updated>2007-08-29T13:57:17-07:00</a10:updated>  
      <a10:rights type="text">Copyright 2007</a10:rights>  
      <a10:content type="text">Item Content</a10:content>  
      <a10:contributor>  
        <a10:name>Lene Aaling</a10:name>  
        <a10:uri>http://Lene/Aaling</a10:uri>  
        <a10:email>Lene@Aaling.com</a10:email>  
      </a10:contributor>  
    </item>  
  </channel>  
</rss>  
```  
  
## <a name="syndicationitem"></a><span data-ttu-id="f424e-118">SyndicationItem</span><span class="sxs-lookup"><span data-stu-id="f424e-118">SyndicationItem</span></span>  
 <span data-ttu-id="f424e-119">下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationItem> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-119">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationItem> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 <span data-ttu-id="f424e-120">下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationItem> 如何序列化為 Atom 1.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-120">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to Atom 1.0.</span></span>  
  
```xml  
<entry xmlns="http://www.w3.org/2005/Atom">  
  <id>ItemID</id>  
  <title type="text">Item Title</title>  
  <summary type="text">Item Summary</summary>  
  <published>2007-08-29T00:00:00-07:00</published>  
  <updated>2007-08-29T14:07:09-07:00</updated>  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
  <author>  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor>  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
  <link rel="alternate" href="http://myitemuri/" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <content type="text">Item Content</content>  
  <rights type="text">Copyright 2007</rights>  
  <source>  
    <title type="text">My Feed Title</title>  
    <subtitle type="text">My Feed Description</subtitle>  
    <link rel="alternate" href="http://myfeeduri/" />  
  </source>  
</entry>  
```  
  
 <span data-ttu-id="f424e-121">下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationItem> 將如何序列化為 RSS 2.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-121">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationItem> is serialized to RSS 2.0.</span></span>  
  
```xml  
<item>  
  <guid isPermaLink="false">ItemID</guid>  
  <link>http://myitemuri/</link>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Jesper Aaberg</name>  
    <uri>http://Jesper/Aaberg</uri>  
    <email>Jesper@Aaberg.com</email>  
  </author>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <category domain="categoryScheme">categoryName</category>  
  <category domain="categoryScheme">categoryName</category>  
  <title>Item Title</title>  
  <description>Item Summary</description>  
  <source>My Feed Title</source>  
  <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
  <updated xmlns="http://www.w3.org/2005/Atom">2007-08-29T14:07:09-07:00</updated>  
  <rights type="text" xmlns="http://www.w3.org/2005/Atom">Copyright 2007</rights>  
  <content type="text" xmlns="http://www.w3.org/2005/Atom">Item Content</content>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
</item>  
```  
  
## <a name="syndicationperson"></a><span data-ttu-id="f424e-122">SyndicationPerson</span><span class="sxs-lookup"><span data-stu-id="f424e-122">SyndicationPerson</span></span>  
 <span data-ttu-id="f424e-123">下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationPerson> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-123">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationPerson> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 <span data-ttu-id="f424e-124">下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationPerson> 如何序列化為 Atom 1.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-124">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> is serialized to Atom 1.0.</span></span>  
  
```xml  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
<contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
```  
  
 <span data-ttu-id="f424e-125">下列 XML 說明如果只有一個 <xref:System.ServiceModel.Syndication.SyndicationPerson> 分別存在於 <xref:System.ServiceModel.Syndication.SyndicationPerson> 或 `Authors` 集合的話，`Contributors` 類別將如何序列化為 RSS 2.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-125">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if only one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 <span data-ttu-id="f424e-126">下列 XML 說明如果有一個以上的 <xref:System.ServiceModel.Syndication.SyndicationPerson> 分別存在於 <xref:System.ServiceModel.Syndication.SyndicationPerson> 或 `Authors` 集合的話，`Contributors` 類別將如何序列化為 RSS 2.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-126">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationPerson> class is serialized to RSS 2.0 if more than one <xref:System.ServiceModel.Syndication.SyndicationPerson> exists in the `Authors` or `Contributors` collections, respectively.</span></span>  
  
```xml  
<a10:author>  
    <a10:name>Jesper Aaberg</a10:name>  
    <a10:uri>http://Contoso/Aaberg</a10:uri>  
    <a10:email>Jesper.Aaberg@contoso.com</a10:email>  
</a10:author>  
<a10:author>  
    <a10:name>Syed Abbas</a10:name>  
    <a10:uri>http://Contoso/Abbas</a10:uri>  
    <a10:email>Syed.Abbas@contoso.com</a10:email>  
</a10:author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
<a10:contributor>  
    <a10:name>Kim Abercrombie</a10:name>  
    <a10:uri>http://Contoso/Abercrombie</a10:uri>  
    <a10:email>Kim.Abercrombie@contoso.com</a10:email>  
</a10:contributor>  
```  
  
## <a name="syndicationlink"></a><span data-ttu-id="f424e-127">SyndicationLink</span><span class="sxs-lookup"><span data-stu-id="f424e-127">SyndicationLink</span></span>  
 <span data-ttu-id="f424e-128">下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationLink> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-128">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationLink> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 <span data-ttu-id="f424e-129">下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationLink> 如何序列化為 Atom 1.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-129">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to Atom 1.0.</span></span>  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 <span data-ttu-id="f424e-130">下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationLink> 將如何序列化為 RSS 2.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-130">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationLink> is serialized to RSS 2.0.</span></span>  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a><span data-ttu-id="f424e-131">SyndicationCategory</span><span class="sxs-lookup"><span data-stu-id="f424e-131">SyndicationCategory</span></span>  
 <span data-ttu-id="f424e-132">下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationCategory> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-132">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.SyndicationCategory> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 <span data-ttu-id="f424e-133">下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationCategory> 如何序列化為 Atom 1.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-133">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to Atom 1.0.</span></span>  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 <span data-ttu-id="f424e-134">下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationCategory> 將如何序列化為 RSS 2.0。</span><span class="sxs-lookup"><span data-stu-id="f424e-134">The following XML shows how the <xref:System.ServiceModel.Syndication.SyndicationCategory> is serialized to RSS 2.0.</span></span>  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a><span data-ttu-id="f424e-135">TextSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="f424e-135">TextSyndicationContent</span></span>  
 <span data-ttu-id="f424e-136">下列程式碼範例說明當您使用 HTML 內容來建立 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 的時候，將 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-136">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with HTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 <span data-ttu-id="f424e-137">下列 XML 說明使用 HTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 Atom 1.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-137">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="html"><html> some html </html></content>`  
  
 <span data-ttu-id="f424e-138">下列 XML 說明使用 HTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-138">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with HTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some html </html></description>`  
  
 <span data-ttu-id="f424e-139">下列程式碼範例說明當您使用純文字內容來建立 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 的時候，將 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-139">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with plain text content.</span></span>  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 <span data-ttu-id="f424e-140">下列 XML 說明使用純文字內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 Atom 1.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-140">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to Atom 1.0.</span></span>  
  
 `<content type="text">Some Plain Text</content>`  
  
 <span data-ttu-id="f424e-141">下列 XML 說明使用純文字內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-141">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with plain text content is serialized to RSS 2.0.</span></span>  
  
 `<description>Some Plain Text</description>`  
  
 <span data-ttu-id="f424e-142">下列程式碼範例說明當您使用 XHTML 內容來建立 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 的時候，將 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-142">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class to Atom 1.0 and RSS 2.0 when <xref:System.ServiceModel.Syndication.TextSyndicationContent> is created with XHTML content.</span></span>  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 <span data-ttu-id="f424e-143">下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 Atom 1.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-143">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to Atom 1.0.</span></span>  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 <span data-ttu-id="f424e-144">下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-144">The following XML shows how the <xref:System.ServiceModel.Syndication.TextSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a><span data-ttu-id="f424e-145">UrlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="f424e-145">UrlSyndicationContent</span></span>  
 <span data-ttu-id="f424e-146">下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.UrlSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-146">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 <span data-ttu-id="f424e-147">下列 XML 說明 <xref:System.ServiceModel.Syndication.UrlSyndicationContent> 類別如何序列化為 Atom 1.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-147">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="audio" src="http://someurl/" />`  
  
 <span data-ttu-id="f424e-148">下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.UrlSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-148">The following XML shows how the <xref:System.ServiceModel.Syndication.UrlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a><span data-ttu-id="f424e-149">XmlSyndicationContent</span><span class="sxs-lookup"><span data-stu-id="f424e-149">XmlSyndicationContent</span></span>  
 <span data-ttu-id="f424e-150">下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.XmlSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-150">The following code example shows how to serialize the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class to Atom 1.0 and RSS 2.0.</span></span>  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 <span data-ttu-id="f424e-151">下列 XML 說明 <xref:System.ServiceModel.Syndication.XmlSyndicationContent> 類別如何序列化為 Atom 1.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-151">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class is serialized to Atom 1.0.</span></span>  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 <span data-ttu-id="f424e-152">下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.XmlSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。</span><span class="sxs-lookup"><span data-stu-id="f424e-152">The following XML shows how the <xref:System.ServiceModel.Syndication.XmlSyndicationContent> class with XHTML content is serialized to RSS 2.0.</span></span>  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a><span data-ttu-id="f424e-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="f424e-153">See Also</span></span>  
 [<span data-ttu-id="f424e-154">WCF 摘要整合概觀</span><span class="sxs-lookup"><span data-stu-id="f424e-154">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [<span data-ttu-id="f424e-155">摘要整合架構</span><span class="sxs-lookup"><span data-stu-id="f424e-155">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 [<span data-ttu-id="f424e-156">如何：建立基本 RSS 摘要</span><span class="sxs-lookup"><span data-stu-id="f424e-156">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 [<span data-ttu-id="f424e-157">如何：建立基本 Atom 摘要</span><span class="sxs-lookup"><span data-stu-id="f424e-157">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 [<span data-ttu-id="f424e-158">如何：將摘要同時公開為 Atom 和 RSS</span><span class="sxs-lookup"><span data-stu-id="f424e-158">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)

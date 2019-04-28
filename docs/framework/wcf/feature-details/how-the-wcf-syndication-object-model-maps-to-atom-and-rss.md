---
title: WCF 新聞訂閱物件模型對應到 Atom 和 RSS 的方式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: b5a7f68edc49a02bb99ca05765d4582b798e72ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855201"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>WCF 新聞訂閱物件模型對應到 Atom 和 RSS 的方式
開發 Windows Communication Foundation (WCF) 的新聞訂閱服務時，您可以建立摘要與項目使用下列類別：  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed> 可以序列化為任何一種用來定義格式器的同步發佈格式。 WCF 隨附兩個格式器：<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>和<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>。  
  
 在 <xref:System.ServiceModel.Syndication.SyndicationFeed> 和 <xref:System.ServiceModel.Syndication.SyndicationItem> 周圍的物件模型會與 Atom 1.0 規格 (而不是 RSS 2.0 規格) 較為符合。 這是因為 Atom 1.0 是比較實質上的規格，可用來定義不明確或是從 RSS 2.0 規格中省略的項目。 因為這個緣故，WCF 新聞訂閱物件模型中的許多項目會在 RSS 2.0 規格中沒有直接的表示法。 當序列化<xref:System.ServiceModel.Syndication.SyndicationFeed>和<xref:System.ServiceModel.Syndication.SyndicationItem>物件至 RSS 2.0 時，WCF 可讓您將 Atom 特定的資料項目序列化為 Atom 規格符合的命名空間限定的延伸模組項目。 您可以將參數傳遞至 <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> 建構函式來控制這個項目。  
  
 本主題中的程式碼範例將使用此處所定義的兩種方法之一來實際執行序列化作業。  
  
 `SerializeFeed` 會序列化新聞訂閱摘要。  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem` 會序列化新聞訂閱項目。  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationFeed> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationFeed> 如何序列化為 Atom 1.0。  
  
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
  
 下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationFeed> 將如何序列化為 RSS 2.0。  
  
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
  
## <a name="syndicationitem"></a>SyndicationItem  
 下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationItem> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationItem> 如何序列化為 Atom 1.0。  
  
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
  
 下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationItem> 將如何序列化為 RSS 2.0。  
  
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
  
## <a name="syndicationperson"></a>SyndicationPerson  
 下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationPerson> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationPerson> 如何序列化為 Atom 1.0。  
  
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
  
 下列 XML 說明如果只有一個 <xref:System.ServiceModel.Syndication.SyndicationPerson> 分別存在於 <xref:System.ServiceModel.Syndication.SyndicationPerson> 或 `Authors` 集合的話，`Contributors` 類別將如何序列化為 RSS 2.0。  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 下列 XML 說明如果有一個以上的 <xref:System.ServiceModel.Syndication.SyndicationPerson> 分別存在於 <xref:System.ServiceModel.Syndication.SyndicationPerson> 或 `Authors` 集合的話，`Contributors` 類別將如何序列化為 RSS 2.0。  
  
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
  
## <a name="syndicationlink"></a>SyndicationLink  
 下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationLink> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationLink> 如何序列化為 Atom 1.0。  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationLink> 將如何序列化為 RSS 2.0。  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.SyndicationCategory> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 下列 XML 會說明 <xref:System.ServiceModel.Syndication.SyndicationCategory> 如何序列化為 Atom 1.0。  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 下列 XML 說明 <xref:System.ServiceModel.Syndication.SyndicationCategory> 將如何序列化為 RSS 2.0。  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 下列程式碼範例說明當您使用 HTML 內容來建立 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 的時候，將 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 下列 XML 說明使用 HTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 Atom 1.0 的方式。  
  
 `<content type="html"><html> some html </html></content>`  
  
 下列 XML 說明使用 HTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。  
  
 `<description><html> some html </html></description>`  
  
 下列程式碼範例說明當您使用純文字內容來建立 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 的時候，將 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 下列 XML 說明使用純文字內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 Atom 1.0 的方式。  
  
 `<content type="text">Some Plain Text</content>`  
  
 下列 XML 說明使用純文字內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。  
  
 `<description>Some Plain Text</description>`  
  
 下列程式碼範例說明當您使用 XHTML 內容來建立 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 的時候，將 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 Atom 1.0 的方式。  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.TextSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.UrlSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 下列 XML 說明 <xref:System.ServiceModel.Syndication.UrlSyndicationContent> 類別如何序列化為 Atom 1.0 的方式。  
  
 `<content type="audio" src="http://someurl/" />`  
  
 下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.UrlSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 下列程式碼範例說明將 <xref:System.ServiceModel.Syndication.XmlSyndicationContent> 類別序列化為 Atom 1.0 與 RSS 2.0 的方式。  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 下列 XML 說明 <xref:System.ServiceModel.Syndication.XmlSyndicationContent> 類別如何序列化為 Atom 1.0 的方式。  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 下列 XML 說明使用 XHTML 內容的 <xref:System.ServiceModel.Syndication.XmlSyndicationContent> 類別將如何序列化為 RSS 2.0 的方式。  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>另請參閱

- [WCF 摘要整合概觀](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [摘要整合架構](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
- [如何：建立基本 RSS 摘要](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)
- [如何：建立基本 Atom 摘要](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)
- [如何：公開 （expose) 的摘要為這兩個 Atom 和 RSS](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)

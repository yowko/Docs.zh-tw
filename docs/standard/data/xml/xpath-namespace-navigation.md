---
title: "XPath 命名空間巡覽"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: beb6265e8b245893cd7fa5edca28ba1b081481ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="c3042-102">XPath 命名空間巡覽</span><span class="sxs-lookup"><span data-stu-id="c3042-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="c3042-103">若要使用 XPath 查詢搭配 XML 文件，您必須正確定址 XML 命名空間以及命名空間所包含的項目。</span><span class="sxs-lookup"><span data-stu-id="c3042-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="c3042-104">命名空間會避免在多個內容中使用名稱時可能發生的模稜兩可。例如，`ID` 名稱可能會參考多個與不同 XML 文件項目相關聯的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c3042-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="c3042-105">命名空間語法會指定 URI、名稱和前置詞，以便區別 XML 文件的項目。</span><span class="sxs-lookup"><span data-stu-id="c3042-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="c3042-106">本主題中的範例將示範如何在透過 <xref:System.Xml.XPath.XPathNavigator> 巡覽 XML 文件時使用前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3042-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="c3042-107">如需有關命名空間和語法的詳細資訊，請參閱[了解 XML 命名空間](http://go.microsoft.com/fwlink/?linkid=140245)。</span><span class="sxs-lookup"><span data-stu-id="c3042-107">For more information about namespaces and syntax, see [Understanding XML Namespaces](http://go.microsoft.com/fwlink/?linkid=140245).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="c3042-108">命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="c3042-108">Namespace Declarations</span></span>  
 <span data-ttu-id="c3042-109">使用 <xref:System.Xml.XPath.XPathNavigator> 的執行個體時，命名空間宣告會讓 XML 文件的項目成為可區別和可定址的項目。</span><span class="sxs-lookup"><span data-stu-id="c3042-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="c3042-110">命名空間前置詞會提供簡短語法來定址命名空間。</span><span class="sxs-lookup"><span data-stu-id="c3042-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="c3042-111">前置詞會依照下列格式定義：`<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.`。在這個語法中，前置詞 "`e`" 是標準命名空間 URI 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="c3042-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="c3042-112">您可以使用 `Body` 語法，將 `Envelope` 項目識別為 `e:Body` 命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="c3042-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="c3042-113">下列 XML 文件將當做下一節巡覽範例中的 `response.xml` 參考。</span><span class="sxs-lookup"><span data-stu-id="c3042-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="c3042-114">依照命名空間前置詞巡覽</span><span class="sxs-lookup"><span data-stu-id="c3042-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="c3042-115">本節中的程式碼會使用 <xref:System.Xml.XPath.XPathNavigator> 和 <xref:System.Xml.XmlNamespaceManager> 物件，從上一節的 XML 文件中選取 `Search` 項目。</span><span class="sxs-lookup"><span data-stu-id="c3042-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="c3042-116">`xpath` 查詢會在路徑中包含每個項目的命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3042-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="c3042-117">指定包含每個項目之命名空間的精確識別可確保 `Search` 方法正確巡覽至 <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 項目。</span><span class="sxs-lookup"><span data-stu-id="c3042-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 <span data-ttu-id="c3042-118">完整限定命名空間和名稱的精確度不僅是為了方便而已。</span><span class="sxs-lookup"><span data-stu-id="c3042-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="c3042-119">如果針對上述範例中的文件定義和程式碼進行一項小實驗，就可確認沒有完整限定項目名稱的巡覽將擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c3042-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="c3042-120">例如，如果項目定義：`<Search xmlns="http://schemas.microsoft.com/v1/Search">` 和查詢字串：`xpath = "/s:Envelope/s:Body/Search";` 沒有 `Search` 項目的命名空間前置詞，就會傳回 `null` 而非 `Search` 項目。</span><span class="sxs-lookup"><span data-stu-id="c3042-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3042-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3042-121">See Also</span></span>  
 [<span data-ttu-id="c3042-122">使用 XPathNavigator 存取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c3042-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="c3042-123">選取、 評估及使用 XPathNavigator 比對 XML 資料</span><span class="sxs-lookup"><span data-stu-id="c3042-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

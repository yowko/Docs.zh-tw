---
title: XslTransform 類別實作 XSLT 處理器
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81d0ce4f697935908b8ad7084560bd1adacbdf2d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705662"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="ca733-102">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="ca733-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="ca733-103"><xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。</span><span class="sxs-lookup"><span data-stu-id="ca733-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="ca733-104">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="ca733-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="ca733-105">如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。</span><span class="sxs-lookup"><span data-stu-id="ca733-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="ca733-106"><xref:System.Xml.Xsl.XslTransform> 類別是可實作 XSL 轉換 (XSLT) 1.0 版建議事項的 XSLT 處理器。</span><span class="sxs-lookup"><span data-stu-id="ca733-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="ca733-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> 方法可尋找及讀取樣式表，而 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法則可轉換指定的來源文件。</span><span class="sxs-lookup"><span data-stu-id="ca733-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="ca733-108">任何實作 <xref:System.Xml.XPath.IXPathNavigable> 介面的存放區都可用來做為 <xref:System.Xml.Xsl.XslTransform> 的來源文件。</span><span class="sxs-lookup"><span data-stu-id="ca733-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="ca733-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 目前可實作 <xref:System.Xml.XPath.IXPathNavigable>、<xref:System.Xml.XmlDocument> 和 <xref:System.Xml.XmlDataDocument> 上的 <xref:System.Xml.XPath.XPathDocument> 介面，因此它們都可用來做為轉換的輸入來源文件。</span><span class="sxs-lookup"><span data-stu-id="ca733-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="ca733-110"><xref:System.Xml.Xsl.XslTransform> 中的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件僅支援 XSLT 1.0 規格，此規格是以下列命名空間定義：</span><span class="sxs-lookup"><span data-stu-id="ca733-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="ca733-111"><xref:System.Xml.Xsl.XslTransform.Load%2A> 方法可用來將下列其中一個類別載入樣式表：</span><span class="sxs-lookup"><span data-stu-id="ca733-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="ca733-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca733-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="ca733-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="ca733-113">XmlReader</span></span>  
  
-   <span data-ttu-id="ca733-114">表示 URL 的字串 </span><span class="sxs-lookup"><span data-stu-id="ca733-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="ca733-115">上述每個輸入類別都有不同的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="ca733-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="ca733-116">有些方法會採用上述其中一個類別與 <xref:System.Xml.XmlResolver> 類別的組合，來做為引數。</span><span class="sxs-lookup"><span data-stu-id="ca733-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="ca733-117"><xref:System.Xml.XmlResolver> 會尋找樣式表中可發現之 `<xsl:import>` 或 `<xsl:include>` 所參考的資源。</span><span class="sxs-lookup"><span data-stu-id="ca733-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="ca733-118">下列幾種方法會採用字串 (<xref:System.Xml.XmlReader>) 或 <xref:System.Xml.XPath.XPathNavigator> 做為輸入。</span><span class="sxs-lookup"><span data-stu-id="ca733-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
```vb  
Overloads Public Sub Load(String)  
```  
  
```csharp  
public void Load(string);  
```  
  
```vb  
Overloads Public Sub Load(String, XmlResolver)  
```  
  
```csharp  
public void Load(string, XmlResolver);  
```  
  
```vb  
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XmlReader, XmlResolver, Evidence);  
```  
  
```vb  
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XPathNavigator, XmlResolver, Evidence);  
```  
  
 <span data-ttu-id="ca733-119">上述 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法大多會以 <xref:System.Xml.XmlResolver> 做為參數。</span><span class="sxs-lookup"><span data-stu-id="ca733-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="ca733-120"><xref:System.Xml.XmlResolver> 可用來載入樣式表，以及 xsl:import 和 xsl:include 項目中所參考的任何樣式表。</span><span class="sxs-lookup"><span data-stu-id="ca733-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="ca733-121">大多數的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法也會以辨識項做為參數。</span><span class="sxs-lookup"><span data-stu-id="ca733-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="ca733-122">辨識項參數是指與樣式表關聯的 <xref:System.Security.Policy.Evidence>。</span><span class="sxs-lookup"><span data-stu-id="ca733-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="ca733-123">樣式表的安全性層級會影響它所參考之後續資源的安全性層級，例如它所包含的指令碼、所使用的任何 `document()` 函式，以及 <xref:System.Xml.Xsl.XsltArgumentList> 所使用的任何擴充物件。</span><span class="sxs-lookup"><span data-stu-id="ca733-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="ca733-124">如果使用 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法 (具有 URL 參數但未提供辨識項) 來載入樣式表，則會結合指定的 URL 與其網站和區域來計算樣式表的辨識項。</span><span class="sxs-lookup"><span data-stu-id="ca733-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="ca733-125">若未提供 URI 或辨識項，則樣式表的辨識項集合將完全受信任。</span><span class="sxs-lookup"><span data-stu-id="ca733-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="ca733-126">請勿從未受信任的來源載入樣式表，或者將未受信任的擴充物件加入 <xref:System.Xml.Xsl.XsltArgumentList> 中。</span><span class="sxs-lookup"><span data-stu-id="ca733-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="ca733-127">如需安全性層級、辨識項，以及辨識項將會如何影響指令碼的詳細資訊，請參閱[使用 \<msxsl:script> 的 XSLT 樣式表指令碼](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)。</span><span class="sxs-lookup"><span data-stu-id="ca733-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="ca733-128">如需安全性層級、辨識項，以及辨識項將會如何影響指令碼的詳細資訊，請參閱[樣式表參數和擴充物件的 XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="ca733-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="ca733-129">如需安全性層級、辨識項，以及辨識項將會如何影響 `document()` 函式的詳細資訊，請參閱[解析外部的 XSLT 樣式表和文件](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md) 。</span><span class="sxs-lookup"><span data-stu-id="ca733-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="ca733-130">可提供樣式表數個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="ca733-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="ca733-131">樣式表也可以呼叫擴充物件上的函式。</span><span class="sxs-lookup"><span data-stu-id="ca733-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="ca733-132">參數和擴充物件都可透過 <xref:System.Xml.Xsl.XsltArgumentList> 類別提供給樣式表。</span><span class="sxs-lookup"><span data-stu-id="ca733-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="ca733-133">如需 <xref:System.Xml.Xsl.XsltArgumentList> 的詳細資訊，請參閱<xref:System.Xml.Xsl.XsltArgumentList>。</span><span class="sxs-lookup"><span data-stu-id="ca733-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="ca733-134">建議的 XslTransform 類別安全使用法</span><span class="sxs-lookup"><span data-stu-id="ca733-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="ca733-135">樣式表的安全性權限取決於所提供的辨識項。</span><span class="sxs-lookup"><span data-stu-id="ca733-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="ca733-136">下表摘錄樣式表的位置，並針對應提供何種辨識項型別加以說明。</span><span class="sxs-lookup"><span data-stu-id="ca733-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="ca733-137">XSLT 樣式表沒有外部參考，或者樣式表是來自您信任的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="ca733-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="ca733-138">從您的組件提供辨識項：</span><span class="sxs-lookup"><span data-stu-id="ca733-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="ca733-139">XSLT 樣式表來自外部來源。</span><span class="sxs-lookup"><span data-stu-id="ca733-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="ca733-140">已知來源的源頭，並且有可驗證的 URI。</span><span class="sxs-lookup"><span data-stu-id="ca733-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="ca733-141">使用 URI 建立辨識項。</span><span class="sxs-lookup"><span data-stu-id="ca733-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="ca733-142">XSLT 樣式表來自外部來源。</span><span class="sxs-lookup"><span data-stu-id="ca733-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="ca733-143">來源的源頭未知。</span><span class="sxs-lookup"><span data-stu-id="ca733-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="ca733-144">將辨識項設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="ca733-144">Set evidence to `null`.</span></span> <span data-ttu-id="ca733-145">不會處理指令碼區塊、不支援 XSLT `document()` 函式，且不允許已授權的擴充物件。</span><span class="sxs-lookup"><span data-stu-id="ca733-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="ca733-146">此外，您也可以將 `resolver` 參數設為 `null`，如此可確保不會處理 `xsl:import` 和 `xsl:include` 項目。</span><span class="sxs-lookup"><span data-stu-id="ca733-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="ca733-147">XSLT 樣式表來自外部來源。</span><span class="sxs-lookup"><span data-stu-id="ca733-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="ca733-148">來源的源頭未知，但是您需要指令碼支援。</span><span class="sxs-lookup"><span data-stu-id="ca733-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="ca733-149">自呼叫端要求識別項。</span><span class="sxs-lookup"><span data-stu-id="ca733-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="ca733-150">XML 資料的轉換</span><span class="sxs-lookup"><span data-stu-id="ca733-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="ca733-151">載入樣式表後，即可呼叫其中一個 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法以及提供輸入來源文件來啟動轉換。</span><span class="sxs-lookup"><span data-stu-id="ca733-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="ca733-152">可多載化 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法，以提供不同的轉換輸出。</span><span class="sxs-lookup"><span data-stu-id="ca733-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="ca733-153">轉換可以產生下列輸出格式：</span><span class="sxs-lookup"><span data-stu-id="ca733-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="ca733-154">檔案的字串 URL</span><span class="sxs-lookup"><span data-stu-id="ca733-154">String URL of file</span></span>  
  
 <span data-ttu-id="ca733-155">字串 URL 是最後一個格式，它經用於 URL 中的輸入文件轉換，以及將文件寫入輸出 URL 等作業案例中。</span><span class="sxs-lookup"><span data-stu-id="ca733-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="ca733-156">這項 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 是一項便利的方法，可從檔案載入 XML 文件，然後執行 XSLT 轉換，再將輸出寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="ca733-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="ca733-157">如此可以防止您必須建立和載入輸入來源文件，再寫入至檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="ca733-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="ca733-158">下列程式碼範例將以字串 URL 做為輸入和輸出，以示範 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法的使用情形：</span><span class="sxs-lookup"><span data-stu-id="ca733-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
```vb  
Dim xsltransform As XslTransform = New XslTransform()  
xsltransform.Load("favorite.xsl")  
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)  
```  
  
```csharp  
XslTransform xsltransform = new XslTransform();  
xsltransform.Load("favorite.xsl");  
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);  
```  
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="ca733-159">轉換 XML 文件的段落</span><span class="sxs-lookup"><span data-stu-id="ca733-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="ca733-160">轉換是指套用到整個文件。</span><span class="sxs-lookup"><span data-stu-id="ca733-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="ca733-161">換言之，如果您要傳入的節點不是文件的根節點，則不會阻止轉換程序取得已載入文件中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="ca733-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="ca733-162">若要轉換結果樹狀結構片段，則必須建立僅包含結果樹狀結構片段的 <xref:System.Xml.XmlDocument>，並將 <xref:System.Xml.XmlDocument> 傳遞至 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="ca733-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="ca733-163">以下範例將執行結果樹狀片段的轉換。</span><span class="sxs-lookup"><span data-stu-id="ca733-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
```vb  
Dim xslt As New XslTransform()  
xslt.Load("print_root.xsl")  
Dim doc As New XmlDocument()  
doc.Load("library.xml")  
' Create a new document containing just the result tree fragment.  
Dim testNode As XmlNode = doc.DocumentElement.FirstChild  
Dim tmpDoc As New XmlDocument()  
tmpDoc.LoadXml(testNode.OuterXml)  
' Pass the document containing the result tree fragment   
' to the Transform method.  
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))  
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)  
```  
  
```csharp  
XslTransform xslt = new XslTransform();       
xslt.Load("print_root.xsl");  
XmlDocument doc = new XmlDocument();  
doc.Load("library.xml");  
// Create a new document containing just the result tree fragment.  
XmlNode testNode = doc.DocumentElement.FirstChild;   
XmlDocument tmpDoc = new XmlDocument();   
tmpDoc.LoadXml(testNode.OuterXml);  
// Pass the document containing the result tree fragment   
// to the Transform method.  
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");  
xslt.Transform(tmpDoc, null, Console.Out, null);  
```  
  
 <span data-ttu-id="ca733-164">此範例使用 library.xml 和 print_root.xsl 檔案做為輸入，並且會將下列項目輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="ca733-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="ca733-165">library.xml</span><span class="sxs-lookup"><span data-stu-id="ca733-165">library.xml</span></span>  
  
```xml  
<library>  
  <book genre='novel' ISBN='1-861001-57-5'>  
     <title>Pride And Prejudice</title>  
  </book>  
  <book genre='novel' ISBN='1-81920-21-2'>  
     <title>Hook</title>  
  </book>  
</library>  
```  
  
 <span data-ttu-id="ca733-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="ca733-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="ca733-167">XSLT 從 .NET Framework 1.0 版到 .NET Framework 1.1 版的轉換</span><span class="sxs-lookup"><span data-stu-id="ca733-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="ca733-168">下列表格將針對 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 方法列出已過時的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版方法以及新的 <xref:System.Xml.Xsl.XslTransform.Load%2A> 1.1 版方法。</span><span class="sxs-lookup"><span data-stu-id="ca733-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="ca733-169">新方法可讓您藉由指定辨識項來限制樣式表的使用權限。</span><span class="sxs-lookup"><span data-stu-id="ca733-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="ca733-170">.NET Framework 1.0 版過時的 Load 方法</span><span class="sxs-lookup"><span data-stu-id="ca733-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="ca733-171">.NET Framework 1.1 版替代的 Load 方法</span><span class="sxs-lookup"><span data-stu-id="ca733-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="ca733-172">Load(XPathNavigator input);</span><span class="sxs-lookup"><span data-stu-id="ca733-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="ca733-173">Load(XPathNavigator input, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="ca733-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="ca733-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="ca733-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="ca733-175">Load(IXPathNavigable stylesheet);</span><span class="sxs-lookup"><span data-stu-id="ca733-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="ca733-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="ca733-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="ca733-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="ca733-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="ca733-178">Load(XmlReader stylesheet);</span><span class="sxs-lookup"><span data-stu-id="ca733-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="ca733-179">Load(XmlReader stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="ca733-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="ca733-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="ca733-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="ca733-181">下列表格將針對 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法列出已過時的方法和新的方法。</span><span class="sxs-lookup"><span data-stu-id="ca733-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="ca733-182">新方法採用的是 <xref:System.Xml.XmlResolver> 物件。</span><span class="sxs-lookup"><span data-stu-id="ca733-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="ca733-183">.NET Framework 1.0 版過時的 Transform 方法 </span><span class="sxs-lookup"><span data-stu-id="ca733-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="ca733-184">.NET Framework 1.1 版替代的 Transform 方法</span><span class="sxs-lookup"><span data-stu-id="ca733-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="ca733-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="ca733-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="ca733-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="ca733-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="ca733-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="ca733-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="ca733-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="ca733-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="ca733-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="ca733-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="ca733-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="ca733-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="ca733-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="ca733-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="ca733-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="ca733-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="ca733-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="ca733-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="ca733-201">Void Transform(String input, String output);</span><span class="sxs-lookup"><span data-stu-id="ca733-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="ca733-202">Void Transform(String input, String output, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="ca733-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="ca733-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> 屬性在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.1 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="ca733-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="ca733-204">請改用新的 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 多載，它採用的是 <xref:System.Xml.XmlResolver> 物件。</span><span class="sxs-lookup"><span data-stu-id="ca733-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca733-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca733-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>  
- [<span data-ttu-id="ca733-206">使用 XslTransform 類別進行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="ca733-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [<span data-ttu-id="ca733-207">轉換中的 XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ca733-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [<span data-ttu-id="ca733-208">轉換中的 XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="ca733-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [<span data-ttu-id="ca733-209">XslTransform 的 XPathDocument 輸入</span><span class="sxs-lookup"><span data-stu-id="ca733-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [<span data-ttu-id="ca733-210">XslTransform 的 XmlDataDocument 輸入</span><span class="sxs-lookup"><span data-stu-id="ca733-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [<span data-ttu-id="ca733-211">XslTransform 的 XmlDocument 輸入</span><span class="sxs-lookup"><span data-stu-id="ca733-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)

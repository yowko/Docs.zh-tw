---
title: XSLT 轉換
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93d45b58433dc3c7231cea741aa7ea67dfab2d7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912029"
---
# <a name="xslt-transformations"></a><span data-ttu-id="11ed1-102">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="11ed1-102">XSLT Transformations</span></span>
<span data-ttu-id="11ed1-103">可延伸樣式表語言轉換 (XSLT) 可讓您將來源 XML 文件的內容轉換成另一種不同格式或結構的文件。</span><span class="sxs-lookup"><span data-stu-id="11ed1-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="11ed1-104">例如，您可以使用 XSLT 將 XML 轉換成網站上使用的 HTML，或將它轉換成只包含應用程式所需欄位的文件。</span><span class="sxs-lookup"><span data-stu-id="11ed1-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="11ed1-105">這項轉換程序是由 [W3C XSL 轉換 (XSLT) 1.0 版建議事項](https://www.w3.org/TR/xslt-10/) (英文) 所指定。</span><span class="sxs-lookup"><span data-stu-id="11ed1-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="11ed1-106"><xref:System.Xml.Xsl.XslCompiledTransform> 類別是 .NET 中的 XSLT 處理程式。</span><span class="sxs-lookup"><span data-stu-id="11ed1-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="11ed1-107"><xref:System.Xml.Xsl.XslCompiledTransform> 類別支援 [W3C XSLT 1.0 建議事項](https://www.w3.org/TR/xslt-10/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="11ed1-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11ed1-108">在 .NET Framework 2.0 版中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。</span><span class="sxs-lookup"><span data-stu-id="11ed1-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="11ed1-109"><xref:System.Xml.Xsl.XslCompiledTransform> 類別是 XSLT 引擎的新實作。</span><span class="sxs-lookup"><span data-stu-id="11ed1-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="11ed1-110">其中包含效能增進與新的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="11ed1-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="11ed1-111">建議的作法是使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別建立 XSLT 應用程式。</span><span class="sxs-lookup"><span data-stu-id="11ed1-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11ed1-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="11ed1-112">In This Section</span></span>  
 [<span data-ttu-id="11ed1-113">使用 XslCompiledTransform 類別</span><span class="sxs-lookup"><span data-stu-id="11ed1-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="11ed1-114">提供有關使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="11ed1-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="11ed1-115">從 XslTransform 類別移轉</span><span class="sxs-lookup"><span data-stu-id="11ed1-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="11ed1-116">討論如何從 <xref:System.Xml.Xsl.XslTransform> 類別移轉程式碼。</span><span class="sxs-lookup"><span data-stu-id="11ed1-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="11ed1-117">XSLT 編譯器 (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="11ed1-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="11ed1-118">提供有關使用 XSLT 編譯器的資訊。</span><span class="sxs-lookup"><span data-stu-id="11ed1-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="11ed1-119">使用 XslTransform 類別進行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="11ed1-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="11ed1-120">提供有關使用 <xref:System.Xml.Xsl.XslTransform> 類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="11ed1-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11ed1-121">參考資料</span><span class="sxs-lookup"><span data-stu-id="11ed1-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="11ed1-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="11ed1-122">Related Sections</span></span>  
 [<span data-ttu-id="11ed1-123">XML 文件和資料</span><span class="sxs-lookup"><span data-stu-id="11ed1-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)

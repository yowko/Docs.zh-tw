---
title: XSLT 轉換
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 92d0af1519260d458d3954beaef38e698142367a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288299"
---
# <a name="xslt-transformations"></a><span data-ttu-id="48685-102">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="48685-102">XSLT Transformations</span></span>
<span data-ttu-id="48685-103">可延伸樣式表語言轉換 (XSLT) 可讓您將來源 XML 文件的內容轉換成另一種不同格式或結構的文件。</span><span class="sxs-lookup"><span data-stu-id="48685-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="48685-104">例如，您可以使用 XSLT 將 XML 轉換成網站上使用的 HTML，或將它轉換成只包含應用程式所需欄位的文件。</span><span class="sxs-lookup"><span data-stu-id="48685-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="48685-105">這項轉換程序是由 [W3C XSL 轉換 (XSLT) 1.0 版建議事項](https://www.w3.org/TR/xslt-10/) (英文) 所指定。</span><span class="sxs-lookup"><span data-stu-id="48685-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="48685-106"><xref:System.Xml.Xsl.XslCompiledTransform> 類別是 .NET 中的 XSLT 處理程式。</span><span class="sxs-lookup"><span data-stu-id="48685-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="48685-107"><xref:System.Xml.Xsl.XslCompiledTransform> 類別支援 [W3C XSLT 1.0 建議事項](https://www.w3.org/TR/xslt-10/) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="48685-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48685-108">在 .NET Framework 2.0 版中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。</span><span class="sxs-lookup"><span data-stu-id="48685-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="48685-109"><xref:System.Xml.Xsl.XslCompiledTransform> 類別是 XSLT 引擎的新實作。</span><span class="sxs-lookup"><span data-stu-id="48685-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="48685-110">其中包含效能增進與新的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="48685-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="48685-111">建議的作法是使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別建立 XSLT 應用程式。</span><span class="sxs-lookup"><span data-stu-id="48685-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="48685-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="48685-112">In This Section</span></span>  
 [<span data-ttu-id="48685-113">使用 XslCompiledTransform 類別</span><span class="sxs-lookup"><span data-stu-id="48685-113">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="48685-114">提供有關使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="48685-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="48685-115">從 XslTransform 類別移轉</span><span class="sxs-lookup"><span data-stu-id="48685-115">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="48685-116">討論如何從 <xref:System.Xml.Xsl.XslTransform> 類別移轉程式碼。</span><span class="sxs-lookup"><span data-stu-id="48685-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="48685-117">XSLT 編譯器 (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="48685-117">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="48685-118">提供有關使用 XSLT 編譯器的資訊。</span><span class="sxs-lookup"><span data-stu-id="48685-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="48685-119">使用 XslTransform 類別進行 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="48685-119">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="48685-120">提供有關使用 <xref:System.Xml.Xsl.XslTransform> 類別的資訊。</span><span class="sxs-lookup"><span data-stu-id="48685-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="48685-121">參考</span><span class="sxs-lookup"><span data-stu-id="48685-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="48685-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="48685-122">Related Sections</span></span>  
 [<span data-ttu-id="48685-123">XML 檔和資料</span><span class="sxs-lookup"><span data-stu-id="48685-123">XML Documents and Data</span></span>](index.md)

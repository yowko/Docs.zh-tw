---
title: 延伸 XSLT 樣式表
ms.date: 03/30/2017
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
ms.openlocfilehash: e598cb497ba1d415a3ccb53f1583352eba4ccdbb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831230"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="37b38-102">延伸 XSLT 樣式表</span><span class="sxs-lookup"><span data-stu-id="37b38-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="37b38-103">本節說明擴充 XSLT 功能的不同方法。</span><span class="sxs-lookup"><span data-stu-id="37b38-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="37b38-104">您可使用 <xref:System.Xml.Xsl.XsltArgumentList> 類別，加入擴充物件或參數。</span><span class="sxs-lookup"><span data-stu-id="37b38-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="37b38-105">然後可從樣式表呼叫該擴充物件或參數。</span><span class="sxs-lookup"><span data-stu-id="37b38-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="37b38-106">此外，您還可使用 `msxsl:script` 項目將指令碼區塊嵌入樣式表中。</span><span class="sxs-lookup"><span data-stu-id="37b38-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37b38-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="37b38-107">In This Section</span></span>  
 [<span data-ttu-id="37b38-108">XSLT 擴充物件</span><span class="sxs-lookup"><span data-stu-id="37b38-108">XSLT Extension Objects</span></span>](xslt-extension-objects.md)  
 <span data-ttu-id="37b38-109">討論如何使用 <xref:System.Xml.Xsl.XsltArgumentList> 類別處理 XSLT 擴充物件。</span><span class="sxs-lookup"><span data-stu-id="37b38-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="37b38-110">XSLT 參數</span><span class="sxs-lookup"><span data-stu-id="37b38-110">XSLT Parameters</span></span>](xslt-parameters.md)  
 <span data-ttu-id="37b38-111">討論如何使用 <xref:System.Xml.Xsl.XsltArgumentList> 類別處理 XSLT 參數。</span><span class="sxs-lookup"><span data-stu-id="37b38-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="37b38-112">使用 msxsl:script 的指令碼區塊</span><span class="sxs-lookup"><span data-stu-id="37b38-112">Script Blocks Using msxsl:script</span></span>](script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="37b38-113">討論如何使用 `msxsl:script` 項目。</span><span class="sxs-lookup"><span data-stu-id="37b38-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37b38-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="37b38-114">Related Sections</span></span>  
 [<span data-ttu-id="37b38-115">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="37b38-115">XSLT Transformations</span></span>](xslt-transformations.md)

---
title: "延伸 XSLT 樣式表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8ccd1a95586bc92bcc712639eded135a69da1a36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="971d7-102">延伸 XSLT 樣式表</span><span class="sxs-lookup"><span data-stu-id="971d7-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="971d7-103">本節說明擴充 XSLT 功能的不同方法。</span><span class="sxs-lookup"><span data-stu-id="971d7-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="971d7-104">您可使用 <xref:System.Xml.Xsl.XsltArgumentList> 類別，加入擴充物件或參數。</span><span class="sxs-lookup"><span data-stu-id="971d7-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="971d7-105">然後可從樣式表呼叫該擴充物件或參數。</span><span class="sxs-lookup"><span data-stu-id="971d7-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="971d7-106">此外，您還可使用 `msxsl:script` 項目將指令碼區塊嵌入樣式表中。</span><span class="sxs-lookup"><span data-stu-id="971d7-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="971d7-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="971d7-107">In This Section</span></span>  
 [<span data-ttu-id="971d7-108">XSLT 擴充物件</span><span class="sxs-lookup"><span data-stu-id="971d7-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="971d7-109">討論如何使用 <xref:System.Xml.Xsl.XsltArgumentList> 類別處理 XSLT 擴充物件。</span><span class="sxs-lookup"><span data-stu-id="971d7-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="971d7-110">XSLT 參數</span><span class="sxs-lookup"><span data-stu-id="971d7-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="971d7-111">討論如何使用 <xref:System.Xml.Xsl.XsltArgumentList> 類別處理 XSLT 參數。</span><span class="sxs-lookup"><span data-stu-id="971d7-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="971d7-112">指令碼區塊使用 msxsl: script</span><span class="sxs-lookup"><span data-stu-id="971d7-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="971d7-113">討論如何使用 `msxsl:script` 項目。</span><span class="sxs-lookup"><span data-stu-id="971d7-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="971d7-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="971d7-114">Related Sections</span></span>  
 [<span data-ttu-id="971d7-115">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="971d7-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)

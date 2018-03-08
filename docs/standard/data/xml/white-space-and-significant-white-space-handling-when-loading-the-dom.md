---
title: "載入 DOM 時處理泛空白字元和顯著泛空白字元"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a16f90b6d48bc2ffabfd678722fa9b6e61328cd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="2cc79-102">載入 DOM 時處理泛空白字元和顯著泛空白字元</span><span class="sxs-lookup"><span data-stu-id="2cc79-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="2cc79-103">載入文件時，您可以設定選項來保留泛空白字元，並且在文件樹狀結構中建立 **XmlWhitespace** 節點。</span><span class="sxs-lookup"><span data-stu-id="2cc79-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="2cc79-104">若要建立泛空白字元節點，請將 **PreserveWhitespace** 屬性設為 True。</span><span class="sxs-lookup"><span data-stu-id="2cc79-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="2cc79-105">如果屬性設為預設的 **false**，就不會建立泛空白字元節點。</span><span class="sxs-lookup"><span data-stu-id="2cc79-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="2cc79-106">顯著泛空白字元節點一定會被保留，而且 **XmlSignificantWhitespace** 節點一律會建立於記憶體中以表示這個資料，無論 **PreserveWhitespace** 旗標的設定為何。</span><span class="sxs-lookup"><span data-stu-id="2cc79-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="2cc79-107">若文件是從讀取器載入，則只有在 **XmlTextReader** 的 **WhitespaceHandling** 屬性未設為 **WhitespaceHandling.None** 時，**XmlDocument** 類別的 **PreserveWhitespace** 旗標屬性設定才會影響 **XmlWhitespace** 節點的建立。</span><span class="sxs-lookup"><span data-stu-id="2cc79-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="2cc79-108">優先順序高於 **XmlDocument** 之旗標設定的，是讀取器上的 **WhitespaceHandling** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="2cc79-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="2cc79-109">如需 **XmlSignificantWhitespace** 的詳細資訊，請參閱 <xref:System.Xml.XmlSignificantWhitespace>。</span><span class="sxs-lookup"><span data-stu-id="2cc79-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc79-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="2cc79-110">See Also</span></span>  
 [<span data-ttu-id="2cc79-111">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="2cc79-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

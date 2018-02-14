---
title: "從讀取器載入資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9e9f934d6bff2c9ff3733551bca89b43920f3104
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="load-data-from-a-reader"></a><span data-ttu-id="927b4-102">從讀取器載入資料</span><span class="sxs-lookup"><span data-stu-id="927b4-102">Load Data from a Reader</span></span>
<span data-ttu-id="927b4-103">使用 <xref:System.Xml.XmlDocument.Load%2A> 方法及 <xref:System.Xml.XmlReader> 的參數載入 XML 文件所發生的行為，與從其他格式載入資料的行為相比會有所不同。</span><span class="sxs-lookup"><span data-stu-id="927b4-103">If an XML document is loaded using the <xref:System.Xml.XmlDocument.Load%2A> method and a parameter of an <xref:System.Xml.XmlReader>, there are differences in the behavior that occurs when compared to the behavior of loading data from the other formats.</span></span> <span data-ttu-id="927b4-104">如果讀取器處於其初始狀態，則 <xref:System.Xml.XmlDocument.Load%2A> 會使用讀取器的整個內容，並利用讀取器中的所有資料建置 XML 文件物件模型 (DOM)。</span><span class="sxs-lookup"><span data-stu-id="927b4-104">If the reader is in its initial state, <xref:System.Xml.XmlDocument.Load%2A> consumes the entire contents from the reader and builds the XML Document Object Model (DOM) from all the data in the reader.</span></span>  
  
 <span data-ttu-id="927b4-105">如果已將讀取器置於文件中某處的節點上，而且隨後將讀取器傳遞至 <xref:System.Xml.XmlDocument.Load%2A> 方法，則 <xref:System.Xml.XmlDocument.Load%2A> 會嘗試將目前節點及其所有同層級節點 (直到關閉目前深度的結束標記) 讀取至記憶體。</span><span class="sxs-lookup"><span data-stu-id="927b4-105">If the reader is already positioned on a node somewhere in the document, and the reader is then passed to the <xref:System.Xml.XmlDocument.Load%2A> method, <xref:System.Xml.XmlDocument.Load%2A> attempts to read the current node and all of its siblings, up to the end tag that closes the current depth into memory.</span></span> <span data-ttu-id="927b4-106">嘗試進行的 <xref:System.Xml.XmlDocument.Load%2A> 是否能夠成功，取決於嘗試載入時讀取器所在的節點，因為 <xref:System.Xml.XmlDocument.Load%2A> 會驗證來自讀取器的 XML 格式是否正確。</span><span class="sxs-lookup"><span data-stu-id="927b4-106">The success of the attempted <xref:System.Xml.XmlDocument.Load%2A> depends on the node that the reader is on when the load is attempted, as <xref:System.Xml.XmlDocument.Load%2A> verifies that the XML from the reader is well-formed.</span></span> <span data-ttu-id="927b4-107">如果 XML 的格式不正確，則 <xref:System.Xml.XmlDocument.Load%2A> 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="927b4-107">If the XML is not well-formed, the <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span> <span data-ttu-id="927b4-108">例如，下列節點集包含兩個根層級的項目，XML 的格式不正確，並且 <xref:System.Xml.XmlDocument.Load%2A> 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="927b4-108">For example, the following set of nodes contain two root-level elements, the XML is not well-formed, and <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span>  
  
-   <span data-ttu-id="927b4-109">Comment 節點之後依次跟隨 Element 節點、Element 節點及 EndElement 節點。</span><span class="sxs-lookup"><span data-stu-id="927b4-109">Comment node, followed by an Element node, followed by an Element node, followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="927b4-110">由於缺少根層級的項目，因此下列節點集會建立不完整的 DOM。</span><span class="sxs-lookup"><span data-stu-id="927b4-110">The following set of nodes creates an incomplete DOM, because there is no root-level element.</span></span>  
  
-   <span data-ttu-id="927b4-111">Comment 節點之後依次跟隨 ProcessingInstruction 節點、Comment 節點及 EndElement 節點。</span><span class="sxs-lookup"><span data-stu-id="927b4-111">Comment node followed by a ProcessingInstruction node followed by a Comment node followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="927b4-112">如此就不會擲回例外狀況，而且會載入資料。</span><span class="sxs-lookup"><span data-stu-id="927b4-112">This does not throw an exception, and the data is loaded.</span></span> <span data-ttu-id="927b4-113">您可以將根項目加入至這些節點的最上層，並建立可正確儲存且格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="927b4-113">You can add a root element to the top of these nodes and create well-formed XML that can be saved without error.</span></span>  
  
 <span data-ttu-id="927b4-114">如果將讀取器置於對文件之根層級而言是無效的分葉節點 (例如，泛空白字元或屬性節點) 上，則讀取器會繼續讀取，直到將其置於可用於根層級的節點上。</span><span class="sxs-lookup"><span data-stu-id="927b4-114">If the reader is positioned on a leaf node that is invalid for the root level of a document (for example, a white space or attribute node), the reader continues to read until it is positioned on a node that can be used for the root.</span></span> <span data-ttu-id="927b4-115">此時文件會開始載入。</span><span class="sxs-lookup"><span data-stu-id="927b4-115">The document begins loading at this point.</span></span>  
  
 <span data-ttu-id="927b4-116">依預設，<xref:System.Xml.XmlDocument.Load%2A> 不會使用文件類型定義 (DTD) 或結構描述驗證，來驗證 XML 是否有效。</span><span class="sxs-lookup"><span data-stu-id="927b4-116">By default, <xref:System.Xml.XmlDocument.Load%2A> does not verify whether the XML is valid using document type definition (DTD) or schema validation.</span></span> <span data-ttu-id="927b4-117">它只會驗證 XML 的格式是否正確。</span><span class="sxs-lookup"><span data-stu-id="927b4-117">It only verifies whether the XML is well-formed.</span></span> <span data-ttu-id="927b4-118">為了執行驗證，您需要使用 <xref:System.Xml.XmlReader> 類別來建立 <xref:System.Xml.XmlReaderSettings>。</span><span class="sxs-lookup"><span data-stu-id="927b4-118">In order for validation to occur, you need to create an <xref:System.Xml.XmlReader> using the <xref:System.Xml.XmlReaderSettings> class.</span></span> <span data-ttu-id="927b4-119"><xref:System.Xml.XmlReader> 類別可以使用 DTD 或結構描述定義語言 (XSD) 結構描述來強制執行驗證。</span><span class="sxs-lookup"><span data-stu-id="927b4-119">The <xref:System.Xml.XmlReader> class can enforce validation using a DTD or Schema definition language (XSD) schema.</span></span> <span data-ttu-id="927b4-120"><xref:System.Xml.ValidationType> 類別上的 <xref:System.Xml.XmlReaderSettings> 屬性可以決定 <xref:System.Xml.XmlReader> 執行個體是否能夠強制執行驗證。</span><span class="sxs-lookup"><span data-stu-id="927b4-120">The <xref:System.Xml.ValidationType> property on the <xref:System.Xml.XmlReaderSettings> class determines whether the <xref:System.Xml.XmlReader> instance enforces validation.</span></span> <span data-ttu-id="927b4-121">如需驗證 XML 資料的詳細資訊，請參閱 <xref:System.Xml.XmlReader> 參考頁面的＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="927b4-121">For more information about validating XML data, see the Remarks section of the <xref:System.Xml.XmlReader> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927b4-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="927b4-122">See Also</span></span>  
 [<span data-ttu-id="927b4-123">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="927b4-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

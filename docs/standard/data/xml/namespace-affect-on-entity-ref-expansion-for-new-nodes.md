---
title: "命名空間對包含項目和屬性的新節點之實體參考擴充的影響"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 39110a9b44e6efbe7ad0331cfdb4fbe6078e7cfc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="7c7cf-102">命名空間對包含項目和屬性的新節點之實體參考擴充的影響</span><span class="sxs-lookup"><span data-stu-id="7c7cf-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="7c7cf-103">因為實體宣告的內容幾乎可包含任何內容，所以內容所包含的項目可能包括 `<!ENTITY aname "<elem>test</elem>">`。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="7c7cf-104">剖析 XML 時，`&aname;` 在剖析期間不會以其取代內容進行擴充。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="7c7cf-105">因為項目的命名空間解析不會發生，所以 XML 不會擴充，除非節點置於文件中。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="7c7cf-106">此時才會知道範圍內的命名空間是什麼。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="7c7cf-107">當節點置於文件中時，會進行命名空間解析，而且產生的實體內容會剖析進它的適當節點。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c7cf-108">一旦擴充發生在新建的實體參考節點上，它就不會再發生了。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="7c7cf-109">因此，項目的取代文字中所使用的命名空間會在設定父節點時產生繫結。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="7c7cf-110">不過，命名空間可以變更現有實體參考節點，當您移除並插入其他地方，或者針對與所複製的實體參考節點**CloneNode**方法。</span><span class="sxs-lookup"><span data-stu-id="7c7cf-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7cf-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c7cf-111">See Also</span></span>  
 [<span data-ttu-id="7c7cf-112">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="7c7cf-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

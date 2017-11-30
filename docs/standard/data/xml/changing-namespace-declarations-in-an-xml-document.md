---
title: "變更 XML 文件中的命名空間宣告"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 627882efcbc41310ee177cba984e4add5b07bd15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="6ee42-102">變更 XML 文件中的命名空間宣告</span><span class="sxs-lookup"><span data-stu-id="6ee42-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="6ee42-103">**XmlDocument**公開命名空間宣告和**xmlns**屬性做為文件物件模型的一部分。</span><span class="sxs-lookup"><span data-stu-id="6ee42-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="6ee42-104">這些儲存在**XmlDocument**，因此當您儲存文件，也可以保留這些屬性的位置。</span><span class="sxs-lookup"><span data-stu-id="6ee42-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="6ee42-105">變更這些屬性會有任何作用**名稱**， **NamespaceURI**，和**首碼**已經在樹狀目錄中的其他節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ee42-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="6ee42-106">例如，如果您載入下列文件，然後在`test`項目具有**NamespaceURI**`123.`</span><span class="sxs-lookup"><span data-stu-id="6ee42-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="6ee42-107">如果您移除`xmlns`屬性，如下所示，然後在`test`項目仍具有**NamespaceURI**的`123`。</span><span class="sxs-lookup"><span data-stu-id="6ee42-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="6ee42-108">同樣地，如果您將加入不同`xmlns`屬性`doc`項目，如下所示，然後在`test`項目仍具有**NamespaceURI** `123`。</span><span class="sxs-lookup"><span data-stu-id="6ee42-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="6ee42-109">因此，變更`xmlns`屬性將會有任何影響，直到您儲存並重新載入**XmlDocument**物件。</span><span class="sxs-lookup"><span data-stu-id="6ee42-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee42-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ee42-110">See Also</span></span>  
 [<span data-ttu-id="6ee42-111">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="6ee42-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

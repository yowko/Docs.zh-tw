---
title: 複製現有節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252866"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="70975-102">複製現有節點</span><span class="sxs-lookup"><span data-stu-id="70975-102">Copy Existing Nodes</span></span>
<span data-ttu-id="70975-103">XML 文件物件模型 (DOM) 中有許多方法和屬性可讓您用來選取節點，如 **SelectSingleNode**、**ChildNodes[int i]**、**Attributes[int i]** 等。</span><span class="sxs-lookup"><span data-stu-id="70975-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="70975-104">一旦選取節點之後，您可以使用處理特殊節點型別的其中一種插入方法，將它插入至樹狀。</span><span class="sxs-lookup"><span data-stu-id="70975-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="70975-105">將節點插入樹狀結構的唯一限制是，文件在節點插入後仍必須保持正確格式。</span><span class="sxs-lookup"><span data-stu-id="70975-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="70975-106">現有節點插入 DOM 樹狀時，即會從它的原始位置移除，然後加入其目標位置中。</span><span class="sxs-lookup"><span data-stu-id="70975-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70975-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70975-107">See also</span></span>

- [<span data-ttu-id="70975-108">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="70975-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

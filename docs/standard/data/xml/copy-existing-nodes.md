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
# <a name="copy-existing-nodes"></a>複製現有節點
XML 文件物件模型 (DOM) 中有許多方法和屬性可讓您用來選取節點，如 **SelectSingleNode**、**ChildNodes[int i]**、**Attributes[int i]** 等。 一旦選取節點之後，您可以使用處理特殊節點型別的其中一種插入方法，將它插入至樹狀。 將節點插入樹狀結構的唯一限制是，文件在節點插入後仍必須保持正確格式。 現有節點插入 DOM 樹狀時，即會從它的原始位置移除，然後加入其目標位置中。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

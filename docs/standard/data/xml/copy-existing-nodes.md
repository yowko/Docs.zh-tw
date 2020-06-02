---
title: 複製現有節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 392490d04ff713529d501e199ac2496ff37de1a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289209"
---
# <a name="copy-existing-nodes"></a>複製現有節點
XML 文件物件模型 (DOM) 中有許多方法和屬性可讓您用來選取節點，如 **SelectSingleNode**、**ChildNodes[int i]**、**Attributes[int i]** 等。 一旦選取節點之後，您可以使用處理特殊節點型別的其中一種插入方法，將它插入至樹狀。 將節點插入樹狀的唯一限制是，文件在節點插入後仍必須保持正確格式。 現有節點插入 DOM 樹狀時，即會從它的原始位置移除，然後加入其目標位置中。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](xml-document-object-model-dom.md)

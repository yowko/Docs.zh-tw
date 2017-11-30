---
title: "複製現有節點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11f3915dfebd7ad9d3144c9bedcd7f42b4754359
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="copy-existing-nodes"></a>複製現有節點
有許多方法和屬性在 XML 文件物件模型 (DOM) 可用來選取節點，例如**SelectSingleNode**， **ChildNodes [int i]**，**屬性 [int i]**. 一旦選取節點之後，您可以使用處理特殊節點型別的其中一種插入方法，將它插入至樹狀。 將節點插入樹狀結構的唯一限制是，文件在節點插入後仍必須保持正確格式。 現有節點插入 DOM 樹狀時，即會從它的原始位置移除，然後加入其目標位置中。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

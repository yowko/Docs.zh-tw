---
title: "XML 文件物件模型 (DOM) 階層架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dec61860fba5815b1dae802d280e8df6628ab91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a>XML 文件物件模型 (DOM) 階層架構
下圖顯示 XML 文件物件模型 (DOM) 的類別階層架構，括弧中有全球資訊網協會 (W3C) 名稱和相關的類別名稱。  
  
 ![XML 文件物件模型 &#40; DOM &#41;階層](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
XML 文件物件模型 (DOM) 階層  
  
 下列類別不會繼承自**XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **XmlNodeChangedEventArgs**  
  
 **XmlImplementation**類別用來建立 XML 文件。 如需詳細資訊，請參閱[建立 XML 文件](../../../../docs/standard/data/xml/xml-document-creation.md)。  
  
 **XmlNamedNodeMap**類別處理未排序的節點集。 如需詳細資訊，請參閱[根據名稱或索引擷取的未排序節點](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)。  
  
 **XmlNodeList**類別處理已排序的節點清單。 如需詳細資訊，請參閱[依索引擷取的已排序節點](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)。  
  
 **XmlNodeChangedEventArgs**類別處理事件處理常式上註冊**XmlDocument**。 如需詳細資訊，請參閱[使用 xmlnodechangedeventargs 之 XML 文件中的事件處理](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)。  
  
 **XmlLinkedNode**類別繼承自**XmlNode**。 其目的是要覆寫兩種方法從**XmlNode**: **PreviousSibling**和**NextSibling**方法。 然後繼承並使用這些覆寫的方法**XmlCharacterData**， **XmlDeclaration**， **XmlDocumentType**， **XmlElement**， **XmlEntityReference**，和**XmlProcessingInstruction**，這些是上一個和下一個同層級成員的類別。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

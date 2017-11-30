---
title: "建立新節點時 XML 項目和屬性名稱的驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c041d5d2830222f3fae09a39f1ea10eb08772388
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>建立新節點時 XML 項目和屬性名稱的驗證
XML 文件物件模型 (DOM) 在建立新項目節點或屬性節點時會檢查名稱的有效性。 如果名稱包含不合法字元，則會擲回例外狀況。 請確認名稱有效，而且編碼正確，您必須使用以**XmlConvert**類別來編碼名稱，並將它解碼回應用程式層級。 **XmlWriter**有方法來執行其他工作，以確保會產生格式正確的 XML。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

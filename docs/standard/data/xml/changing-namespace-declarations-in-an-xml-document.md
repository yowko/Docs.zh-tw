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
# <a name="changing-namespace-declarations-in-an-xml-document"></a>變更 XML 文件中的命名空間宣告
**XmlDocument**公開命名空間宣告和**xmlns**屬性做為文件物件模型的一部分。 這些儲存在**XmlDocument**，因此當您儲存文件，也可以保留這些屬性的位置。 變更這些屬性會有任何作用**名稱**， **NamespaceURI**，和**首碼**已經在樹狀目錄中的其他節點的屬性。 例如，如果您載入下列文件，然後在`test`項目具有**NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 如果您移除`xmlns`屬性，如下所示，然後在`test`項目仍具有**NamespaceURI**的`123`。  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 同樣地，如果您將加入不同`xmlns`屬性`doc`項目，如下所示，然後在`test`項目仍具有**NamespaceURI** `123`。  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 因此，變更`xmlns`屬性將會有任何影響，直到您儲存並重新載入**XmlDocument**物件。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

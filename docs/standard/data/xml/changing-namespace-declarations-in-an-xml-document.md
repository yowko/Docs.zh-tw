---
title: 變更 XML 文件中的命名空間宣告
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa41e8a4e8f5a15d789ddc81c2b94072c6f16b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>變更 XML 文件中的命名空間宣告
**XmlDocument** 公開命名空間宣告，而且 **xmlns** 屬性是文件物件模型的一部份。 這些是儲存在 **XmlDocument** 中，因此當您儲存文件時，它可以保留那些屬性的位置。 變更這些屬性對已經存在於樹狀結構中之節點的 **Name**、**NamespaceURI** 和 **Prefix** 屬性並沒有影響。 例如，如果載入下列文件，則 `test` 項目會具有 **NamespaceURI** `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 如果如下所示移除 `xmlns` 屬性，則 `test` 項目仍會具有 `123` 的 **NamespaceURI**。  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 同樣地，如果如下所示將不同的 `xmlns` 屬性加入 `doc` 項目，則 `test` 項目仍會具有 **NamespaceURI** `123`。  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 因此，除非儲存並重新載入 **XmlDocument** 物件，否則變更 `xmlns` 屬性並不會產生任何影響。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

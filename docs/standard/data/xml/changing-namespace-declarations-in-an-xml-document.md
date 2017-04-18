---
title: "變更 XML 文件中的命名空間宣告 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 變更 XML 文件中的命名空間宣告
**XmlDocument** 公開命名空間宣告，而且 **xmlns** 屬性是文件物件模型的一部份。  這些是儲存在 **XmlDocument** 中，因此當您儲存文件時，它可以保留這些屬性的位置。  變更這些屬性對已經存在於樹狀結構中之節點的 **Name**、**NamespaceURI** 和 **Prefix** 屬性並沒有影響。  例如，如果載入下列文件，則 `test` 項目會具有 **NamespaceURI** `123.`  
  
```  
<test xmlns="123"/>  
```  
  
 如果如下所示移除 `xmlns` 屬性，則 `test` 項目仍會具有 **NamespaceURI** 值 `123`。  
  
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
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
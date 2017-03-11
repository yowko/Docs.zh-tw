---
title: "GetXmlNamespace Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.GetXmlNamespace"
  - "GetXmlNamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetXmlNamespace operator"
  - "GetXmlNamespace keyword"
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# GetXmlNamespace Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

取得 <xref:System.Xml.Linq.XNamespace> 物件，該物件對應於指定的 XML 命名空間前置字元。  
  
## 語法  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## 組件  
 `xmlNamespacePrefix`  
 選擇項。  可識別 XML 命名空間前置字元的字串。  如果提供，此字串必須是有效的 XML 識別項。  如需詳細資訊，請參閱 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。  如果未指定前置字元，會傳回預設命名空間。  如果未指定預設命名空間，則會傳回空的命名空間。  
  
## 傳回值  
 <xref:System.Xml.Linq.XNamespace> 物件對應於 XML 命名空間前置字元。  
  
## 備註  
 `GetXmlNamespace` 運算子會取得 <xref:System.Xml.Linq.XNamespace> 物件，該物件對應於 XML 命名空間前置字元 `xmlNamespacePrefix`。  
  
 您可以在 XML 常值和 XML 軸屬性中直接使用 XML 命名空間前置字元。  但是，您必須先使用 `GetXmlNamespace` 運算子將命名空間前置字元轉換為 <xref:System.Xml.Linq.XNamespace> 物件，之後才能在程式碼中使用。  您可以將未限定的項目名稱附加至 <xref:System.Xml.Linq.XNamespace> 物件以取得完整限定的 <xref:System.Xml.Linq.XName> 物件，該物件是許多 [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 方法所需的物件。  
  
## 範例  
 下列範例將 `ns` 匯入為 XML 命名空間前置字元。  然後使用這個命名空間前置字元建立 XML 常值，並且存取具有限定名稱 `ns:phone` 的第一個子節點。  之後將該子節點傳遞至 `ShowName` 副程式，該副程式會使用 `GetXmlNamespace` 運算子建構限定名稱。  然後 `ShowName` 副程式會將限定名稱傳遞至 <xref:System.Xml.Linq.XNode.Ancestors%2A> 方法以取得父代 `ns:contact` 節點。  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/getxmlnamespace-operator_1.vb)]  
  
 當您呼叫 `TestGetXmlNamespace.RunSample()` 時，會顯示包含下列文字的訊息方塊：  
  
 `Name: Patrick Hines`  
  
## 請參閱  
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Accessing XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
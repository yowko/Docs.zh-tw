---
title: "XML CDATA Literal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralCdata"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "CDATA literal [Visual Basic]"
  - "XML CDATA literal [Visual Basic]"
  - "XML literals [Visual Basic], CDATA"
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# XML CDATA Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

表示 <xref:System.Xml.Linq.XCData> 物件的常值 \(Literal\)。  
  
## 語法  
  
```  
<![CDATA[content]]>  
```  
  
## 組件  
 `<![CDATA[`  
 必要項。  代表 XML CDATA 區段的開始。  
  
 `content`  
 必要項。  XML CDATA 區段中顯示的文字內容。  
  
 `]]>`  
 必要項。  代表區段的結尾。  
  
## 傳回值  
 <xref:System.Xml.Linq.XCData> 物件。  
  
## 備註  
 XML CDATA 區段包含應該納入、但不應剖析的未經處理文字，以及包含這段文字的 XML。  XML CDATA 區段可以包含任何文字，  包括應保留的 XML 字元。  XML CDATA 區段以 "\]\]\>" 字串結尾。  這暗示了下列幾點：  
  
-   您不能在 XML CDATA 常值中使用內嵌運算式，原因是內嵌運算式分隔符號 \(Delimiter\) 是有效的 XML CDATA 內容。  
  
-   XML CDATA 區段不可以是巢狀，原因是 `content` 不能包含 "\]\]\>" 值。  
  
 您可以將 XML CDATA 常值指派給變數，也可以將它加入至 XML 項目常值中。  
  
> [!NOTE]
>  XML 常值可以在不使用行接續字元 \(Line Continuation Character\) 的情況下跨越數行。  這可讓您複製 XML 文件中的內容，並直接貼上至 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將 XML CDATA 常值轉換為對 <xref:System.Xml.Linq.XCData.%23ctor%2A> 建構函式的呼叫。  
  
## 範例  
 下列範例會建立包含文字 "Can contain literal \<XML\> tags" 的 CDATA 區段。  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-cdata-literal_1.vb)]  
  
## 請參閱  
 <xref:System.Xml.Linq.XCData>   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
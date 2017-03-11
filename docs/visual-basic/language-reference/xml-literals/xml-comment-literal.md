---
title: "XML Comment Literal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "comment literal [Visual Basic]"
  - "XML comments, adding [Visual Basic]"
  - "XML comment literal [Visual Basic]"
  - "XML literals [Visual Basic], comment"
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# XML Comment Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

表示 <xref:System.Xml.Linq.XComment> 物件的常值。  
  
## 語法  
  
```  
<!-- content -->  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`<!--`|必要項。  代表 XML 註解的開始。|  
|`content`|必要項。  XML 註解中要顯示的文字。  不能連續包含兩個連字號 \(\-\-\)，也不能在結尾標記旁加上連字號做為結尾。|  
|`-->`|必要項。  代表 XML 註解的結尾。|  
  
## 傳回值  
 <xref:System.Xml.Linq.XComment> 物件。  
  
## 備註  
 XML 註解常值包含的不是文件內容，而是文件的相關資訊。  XML 註解區段會以 "\-\-\>" 字串結尾。  這暗示了下列幾點：  
  
-   您不能在 XML 註解常值中使用內嵌運算式，原因是內嵌運算式分隔符號 \(Delimiter\) 是有效的 XML 註解內容。  
  
-   XML 註解區段不可以是巢狀，原因是 `content` 不能包含 "\-\-\>" 值。  
  
 您可以將 XML 註解常值指派給變數，也可以將它加入至 XML 項目常值中。  
  
> [!NOTE]
>  XML 常值 \(Literal\) 可以在不需使用行接續字元的情況下跨越數行。  這項功能可讓您複製 XML 文件中的內容，並直接貼上至 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將 XML 註解常值轉換為對 <xref:System.Xml.Linq.XComment.%23ctor%2A> 建構函式的呼叫。  
  
## 範例  
 下列範例會建立 XML 註解，其中包含 "This is a comment" 文字。  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-comment-literal_1.vb)]  
  
## 請參閱  
 <xref:System.Xml.Linq.XComment>   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
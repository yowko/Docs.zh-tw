---
title: "XML Processing Instruction Literal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralProcessingInstruction"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML literals [Visual Basic], processing instruction"
  - "XML processing instruction literal [Visual Basic]"
  - "processing instruction literal [Visual Basic]"
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# XML Processing Instruction Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

表示 <xref:System.Xml.Linq.XProcessingInstruction> 物件的常值 \(Literal\)。  
  
## 語法  
  
```  
<?piName [ = piData ] ?>  
```  
  
## 組件  
 `<?`  
 必要項。  代表 XML 處理指示常值的開始。  
  
 `piName`  
 必要項。  指出處理指示應以哪個應用程式做為目標的名稱。  無法以 "xml" 或 "XML" 做為開頭。  
  
 `piData`  
 選擇項。  一個字串，指出由 `piName` 鎖定目標的應用程式應如何處理 XML 文件。  
  
 `?>`  
 必要項。  代表處理指示的結尾。  
  
## 傳回值  
 <xref:System.Xml.Linq.XProcessingInstruction> 物件。  
  
## 備註  
 XML 處理指示常值會指出應用程式應如何處理 XML 文件。  當應用程式載入 XML 文件時，應用程式可以檢查 XML 處理指示以判斷如何處理文件。  應用程式會轉譯 `piName` 和 `piData` 的意義。  
  
 XML 文件常值使用的語法與 XML 處理指示的語法類似。  如需詳細資訊，請參閱 [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
> [!NOTE]
>  `piName` 項目無法以字串 "xml" 或 "XML" 做為開頭，因為 XML 1.0 規格保留了這些識別項。  
  
 您可以將 XML 處理指示常值指派給變數，或將它加入至 XML 文件常值中。  
  
> [!NOTE]
>  XML 常值可以在不需使用行接續字元的情況下跨越數行。  這可讓您複製 XML 文件中的內容，並直接貼上至 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器 \(Compiler\) 會將 XML 處理指示常值轉換為對 <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> 建構函式 \(Constructor\) 的呼叫。  
  
## 範例  
 下列範例建立處理指示，會識別 XML 文件的樣式表。  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-processing-instructi_1.vb)]  
  
## 請參閱  
 <xref:System.Xml.Linq.XProcessingInstruction>   
 [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
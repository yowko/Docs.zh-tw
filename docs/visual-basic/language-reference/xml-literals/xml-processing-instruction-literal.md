---
title: "XML 處理指示常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
dev_langs:
- VB
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2903297fa22cd8dc10bc4b12abaa754d4f6284f2
ms.lasthandoff: 03/13/2017

---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 處理指示常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XProcessingInstruction>物件。</xref:System.Xml.Linq.XProcessingInstruction>  
  
## <a name="syntax"></a>語法  
  
```  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>組件  
 `<?`  
 必要項。 代表 XML 處理指示常值開始。  
  
 `piName`  
 必要項。 名稱指出哪個應用程式處理指示目標。 不能以"xml"或"XML"開頭。  
  
 `piData`  
 選擇項。 字串，表示應用程式的目標的方式`piName`應該處理 XML 文件。  
  
 `?>`  
 必要項。 代表處理指示的結尾。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XProcessingInstruction>物件。</xref:System.Xml.Linq.XProcessingInstruction>  
  
## <a name="remarks"></a>備註  
 XML 處理指示常值會指出應用程式應該如何處理 XML 文件。 當應用程式載入 XML 文件時，應用程式可以檢查以決定如何處理文件的 XML 處理指示。 應用程式會將解譯的意義`piName`和`piData`。  
  
 XML 文件常值會使用類似的 XML 處理指示的語法。 如需詳細資訊，請參閱[XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
> [!NOTE]
>  `piName`項目開頭的字串"xml"或"XML"，因為 XML 1.0 規格會保留這些識別項。  
  
 您可以指派給變數的 XML 處理指示常值或將它包含在 XML 文件常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行程式碼，而不需要行接續字元。 這可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 處理指示常值轉換成呼叫<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>  
  
## <a name="example"></a>範例  
 下列範例會建立用來識別 XML 文件樣式表處理指示。  
  
 [!code-vb[VbXMLSamples #&28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>   
 [XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)   
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

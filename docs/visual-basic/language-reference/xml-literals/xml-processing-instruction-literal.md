---
title: "XML 處理指示常值 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ce0f2d0dff80072beefdb4f84643ea28e2cf165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>XML 處理指示常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XProcessingInstruction>物件。  
  
## <a name="syntax"></a>語法  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>組件  
 `<?`  
 必要項。 代表 XML 處理指示常值的開始。  
  
 `piName`  
 必要項。 名稱指出哪個應用程式處理指示目標。 無法以"xml"或"XML"開頭。  
  
 `piData`  
 選擇項。 字串，表示如何在應用程式做為目標`piName`應該處理 XML 文件。  
  
 `?>`  
 必要項。 代表處理指示的結尾。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XProcessingInstruction> 物件。  
  
## <a name="remarks"></a>備註  
 XML 處理指示常值會指出應用程式應該如何處理 XML 文件。 當應用程式載入的 XML 文件時，應用程式可以檢查以決定如何處理文件的 XML 處理指示。 應用程式會將解譯的意義`piName`和`piData`。  
  
 XML 文件常值會使用類似的 XML 處理指示的語法。 如需詳細資訊，請參閱[XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
> [!NOTE]
>  `piName`與字串"xml"或"XML"，無法開始項目，因為 XML 1.0 規格會保留這些識別項。  
  
 您可以指派給變數的 XML 處理指示常值，或將它包含在 XML 文件常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行，而不需行接續字元。 這可讓您從 XML 文件內容複製並貼上直接將[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器會將 XML 處理指示常值轉換成呼叫<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>建構函式。  
  
## <a name="example"></a>範例  
 下列範例會建立用來識別 XML 文件樣式表處理指示。  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [XML 文件常值](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)

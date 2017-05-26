---
title: "屬性清單 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e360794ad217784e2358967bfbcc03959cd043b1
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="attribute-list-visual-basic"></a>屬性清單 (Visual Basic)
指定要套用至宣告的程式設計項目屬性。 以逗號分隔多個屬性。 以下是一個屬性的語法。  
  
## <a name="syntax"></a>語法  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>組件  
 `attributemodifier`  
 所需的原始程式檔的開頭套用的屬性。 可以是[組件](../../../visual-basic/language-reference/modifiers/assembly.md)或[模組](../../../visual-basic/language-reference/modifiers/module-keyword.md)。  
  
 `attributename`  
 必要項。 屬性的名稱。  
  
 `attributearguments`  
 選擇項。 這個屬性的位置引數的清單。 以逗號分隔多個引數。  
  
 `attributeinitializer`  
 選擇項。 這個屬性的變數或屬性初始設定式清單。 以逗號分隔多個初始設定式。  
  
## <a name="remarks"></a>備註  
 您可以套用一個或多個屬性，大部分的程式設計項目 （類型、 程序、 屬性和其他等等）。 屬性會顯示在您的組件中繼資料，並可協助您加上註解您的程式碼，或指定如何使用特定的程式設計項目。 您可以套用 Visual Basic 和.NET Framework 中，所定義的屬性，而且您可以定義自己的屬性。  

 如需何時使用屬性的詳細資訊，請參閱[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)。 如需屬性名稱的資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="rules"></a>規則  
  
-   **放置。** 您可以將屬性套用至大部分已宣告的程式設計項目。 若要套用一或多個屬性，您將*屬性區塊*項目宣告的開頭。 屬性清單中的每個項目會指定您想要套用的屬性和修飾詞和您要用於屬性的這個引動過程的引數。  
  
-   **角括號。** 如果您提供的屬性清單，您必須將它括在角括弧 ("`<`"和"`>`")。  
  
-   **宣告的一部分。** 屬性必須是項目宣告，而不是個別的陳述式的一部分。 您可以使用行接續序列 (「 `_`」) 來延伸到多個原始程式行的宣告陳述式。  
  
-   **修飾詞。** 屬性修飾詞 (`Assembly`或`Module`) 需要在每個屬性套用至原始程式檔的開頭的程式設計項目。 不允許屬性修飾詞套用至不在原始程式檔開頭的項目。  
  
-   **引數。** 屬性的所有位置引數必須在之前的任何變數或屬性初始設定式。  
  
## <a name="example"></a>範例  
 下列範例會套用<xref:System.Runtime.InteropServices.DllImportAttribute>屬性的基本架構定義`Function`程序。</xref:System.Runtime.InteropServices.DllImportAttribute>  
  
 [!code-vb[VbVbalrStatements #&1;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>表示屬性化的程序會表示 unmanaged 動態連結程式庫 (DLL) 中的進入點。</xref:System.Runtime.InteropServices.DllImportAttribute> 屬性會提供 DLL 名稱做為位置引數和變數初始設定式的其他資訊。  
  
## <a name="see-also"></a>另請參閱  
 [組件](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [模組\<關鍵字 >](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [如何：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)


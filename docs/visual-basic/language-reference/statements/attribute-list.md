---
title: 屬性清單 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="attribute-list-visual-basic"></a>屬性清單 (Visual Basic)
指定要套用至程式設計項目宣告的屬性。 以逗號分隔多個屬性。 以下是一個屬性的語法。  
  
## <a name="syntax"></a>語法  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>組件  
 `attributemodifier`  
 需要套用的原始程式檔開頭的屬性。 可以是[組件](../../../visual-basic/language-reference/modifiers/assembly.md)或[模組](../../../visual-basic/language-reference/modifiers/module-keyword.md)。  
  
 `attributename`  
 必要。 屬性的名稱。  
  
 `attributearguments`  
 選擇性。 這個屬性的位置引數的清單。 以逗號分隔多個引數。  
  
 `attributeinitializer`  
 選擇性。 這個屬性的變數或屬性初始設定式清單。 以逗號分隔多個初始設定式。  
  
## <a name="remarks"></a>備註  
 您可以將一或多個屬性套用至幾乎任何程式設計項目 （類型、 程序、 屬性和其他等等）。 屬性出現在組件的中繼資料，而且它們可以協助您標註程式碼，或指定如何使用特定的程式設計項目。 您可以套用 Visual Basic 和.NET Framework 中，所定義的屬性，而且您可以定義您自己的屬性。  

 如需何時使用屬性的詳細資訊，請參閱[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)。 如需屬性名稱的資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="rules"></a>規則  
  
-   **放置。** 您可以將屬性套用至大部分已宣告的程式設計項目。 若要套用一個或多個屬性，您將*屬性區塊*項目宣告的開頭。 在屬性清單中的每個項目會指定您想要套用的屬性的修飾詞和您使用這個引動過程屬性的引數。  
  
-   **角括號。** 如果您提供的屬性清單時，您必須將它括在角括號 ("`<`"和"`>`")。  
  
-   **宣告的一部分。** 屬性必須是項目宣告，而不是個別的陳述式的一部分。 您可以使用行接續序列 (" `_`」) 來擴充宣告陳述式分成多個原始程式行。  
  
-   **修飾詞。** 屬性修飾詞 (`Assembly`或`Module`) 需要在每個套用至程式設計項目在原始程式檔開頭的屬性。 在屬性套用至不在原始程式檔開頭的項目上不允許屬性修飾詞。  
  
-   **引數。** 屬性的所有位置引數必須在前面的任何變數或屬性初始設定式。  
  
## <a name="example"></a>範例  
 下列範例會套用<xref:System.Runtime.InteropServices.DllImportAttribute>屬性的基本架構定義`Function`程序。  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 表示屬性化的程序會表示 unmanaged 動態連結程式庫 (DLL) 中的進入點。 屬性會提供 DLL 名稱做為位置的引數和變數初始設定式的其他資訊。  
  
## <a name="see-also"></a>另請參閱  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [Module \<鍵字>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [操作說明：在程式碼內中斷和合併陳述式](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

---
title: 屬性清單
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f2400334182d373ea49c130fd17bc4f9943248d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408441"
---
# <a name="attribute-list-visual-basic"></a>屬性清單 (Visual Basic)
指定要套用至宣告的程式設計項目的屬性。 以逗號分隔多個屬性。 以下是一個屬性的語法。  
  
## <a name="syntax"></a>語法  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>組件  
|||
|---|---|
|`attributemodifier`|在原始程式檔開頭套用之屬性的必要項。 可以是[元件](../modifiers/assembly.md)或[模組](../modifiers/module-keyword.md)。|
|`attributename`| 必要。 屬性的名稱。|
|`attributearguments`|選擇性。 這個屬性的位置引數清單。 以逗號分隔多個引數。|
|`attributeinitializer`|選擇性。 這個屬性的變數或屬性初始化運算式清單。 多個初始化運算式會以逗號分隔。|
  
## <a name="remarks"></a>備註  
 您可以將一個或多個屬性套用至幾乎任何程式設計項目（類型、程式、屬性等等）。 屬性會出現在元件的中繼資料中，並可協助您標注程式碼，或指定如何使用特定的程式設計項目。 您可以套用 Visual Basic 和 .NET Framework 所定義的屬性，而且您可以定義自己的屬性。  

 如需何時使用屬性的詳細資訊，請參閱[屬性總覽](../../programming-guide/concepts/attributes/index.md)。 如需屬性名稱的資訊，請參閱宣告的[元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="rules"></a>規則  
  
- **粘貼.** 您可以將屬性（attribute）套用至大部分宣告的程式設計項目。 若要套用一個或多個屬性，您可以將*屬性區塊*放在元素宣告的開頭。 [屬性] 清單中的每個專案會指定您想要套用的屬性，以及您在此屬性調用中使用的修飾詞和引數。  
  
- **角括弧。** 如果您提供屬性清單，則必須將它括在角括弧（" `<` " 和 " `>` "）中。  
  
- **宣告的一部分。** 屬性必須是元素宣告的一部分，而不是個別的語句。 您可以使用行接續序列（" `_` "），將宣告語句擴充到多個源程式碼。  
  
- **修改.** 在原始程式檔 `Assembly` 開頭套用至程式設計專案的 `Module` 每個屬性上，都需要屬性修飾詞（或）。 屬性修飾詞不能用於套用至不在原始程式檔開頭之元素的屬性。  
  
- **參量.** 屬性的所有位置引數都必須在任何變數或屬性初始化運算式之前。  
  
## <a name="example"></a>範例  
 下列範例會將屬性套用至程式的基本架構 <xref:System.Runtime.InteropServices.DllImportAttribute> 定義 `Function` 。  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>指出屬性化程式代表非受控動態連結程式庫（DLL）中的進入點。 屬性會提供 DLL 名稱做為位置引數，並將其他資訊當做變數初始化運算式。  
  
## <a name="see-also"></a>另請參閱

- [組件](../modifiers/assembly.md)
- [Module\<keyword>](../modifiers/module-keyword.md)
- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
- [作法：程式碼中的 Break 及 Combine 陳述式](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

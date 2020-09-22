---
title: 屬性清單
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: e566239c56efa8ca8e83bff92486fec4c434e92b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874745"
---
# <a name="attribute-list-visual-basic"></a>屬性清單 (Visual Basic)

指定要套用至宣告的程式設計專案的屬性。 以逗號分隔多個屬性。 以下是一個屬性的語法。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>組件  

|||
|---|---|
|`attributemodifier`|在原始程式檔開頭套用的屬性需要。 可以是 [元件](../modifiers/assembly.md) 或 [模組](../modifiers/module-keyword.md)。|
|`attributename`| 必要。 屬性的名稱。|
|`attributearguments`|選擇性。 這個屬性的位置引數清單。 多個引數會以逗號分隔。|
|`attributeinitializer`|選擇性。 這個屬性的變數或屬性初始化運算式清單。 多個初始化運算式會以逗號分隔。|
  
## <a name="remarks"></a>備註  

 您可以將一或多個屬性套用至幾乎任何程式設計項目， (類型、程式、屬性等等) 。 屬性會出現在元件的中繼資料中，並可協助您為程式碼加上批註，或指定如何使用特定的程式設計專案。 您可以套用 Visual Basic 和 .NET Framework 所定義的屬性，也可以定義自己的屬性。  

 如需何時使用屬性的詳細資訊，請參閱 [屬性總覽](../../programming-guide/concepts/attributes/index.md)。 如需屬性名稱的詳細資訊，請參閱宣告的 [元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="rules"></a>規則  
  
- **位置。** 您可以將屬性套用至大部分宣告的程式設計項目。 若要套用一或多個屬性，請在元素宣告的開頭放置 *屬性區塊* 。 屬性清單中的每個專案都會指定您要套用的屬性，以及您在此屬性調用中使用的修飾詞和引數。  
  
- **角括弧。** 如果您提供屬性清單，則必須將它括在角括弧中 ( " `<` " 和 " `>` " ) 。  
  
- **宣告的一部分。** 屬性必須是元素宣告的一部分，而不是個別的語句。 您可以使用行接續順序 ( " `_` " ) 將宣告語句延伸至多個源程式碼。  
  
- **修飾 符。** 在原始程式檔 `Assembly` 開頭套用至程式設計專案的 `Module` 每個屬性都需要屬性修飾詞 (或) 。 在不是原始程式檔開頭的專案套用的屬性上，不允許屬性修飾詞。  
  
- **參數。** 屬性的所有位置引數都必須在任何變數或屬性初始化運算式之前。  
  
## <a name="example"></a>範例  

 下列範例會將屬性套用至程式的基本架構 <xref:System.Runtime.InteropServices.DllImportAttribute> 定義 `Function` 。  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 表示屬性化程式代表非受控動態連結程式庫中的進入點， (DLL) 。 屬性提供 DLL 名稱做為位置引數，而其他資訊則做為變數初始化運算式。  
  
## <a name="see-also"></a>另請參閱

- [組件](../modifiers/assembly.md)
- [模組 \<keyword>](../modifiers/module-keyword.md)
- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
- [作法：程式碼中的 Break 及 Combine 陳述式](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

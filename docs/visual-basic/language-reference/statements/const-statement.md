---
title: Const 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 522ac71767707ae90a3f1d11d45ef8b29471ae6c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005119"
---
# <a name="const-statement-visual-basic"></a>Const 陳述式 (Visual Basic)
宣告並定義一或多個常數。  
  
## <a name="syntax"></a>語法  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>組件  
 `attributelist`  
 選擇性。 套用至此語句中宣告之所有常數的屬性清單。 請參閱以角括弧括住的[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)（"`<`" 和 "`>`"）。  
  
 `accessmodifier`  
 選擇性。 使用此項來指定哪些程式碼可以存取這些常數。 可以是[公用](../../../visual-basic/language-reference/modifiers/public.md)、[受保護](../../../visual-basic/language-reference/modifiers/protected.md)、 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)、[受保護的 Friend](../modifiers/protected-friend.md)、[私](../../../visual-basic/language-reference/modifiers/private.md)用或[私用保護](../../language-reference/modifiers/private-protected.md)。
  
 `Shadows`  
 選擇性。 使用此專案來重新宣告和隱藏基類中的程式設計項目。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
 `constantlist`  
 必要項。 在此語句中宣告的常數清單。  
  
 `constant` `[ ,` `constant` `... ]`  
  
 每個 `constant` 都具有下列語法和組件：  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|組件|描述|  
|----------|-----------------|  
|`constantname`|必要項。 常數的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`datatype`|如果 `Option Strict` `On` 則為必要。 常數的資料類型。|  
|`initializer`|必要項。 在編譯時期評估並指派給常數的運算式。|  
  
## <a name="remarks"></a>備註  
 如果您的應用程式中有永不變更的值，您可以定義已命名的常數，並將其取代為常值。 名稱比值更容易記住。 您可以只定義常數一次，並將其用於程式碼中的許多位置。 如果在較新的版本中，您必須重新定義值，則 `Const` 語句是您唯一需要進行變更的位置。  
  
 您只能在模組或程式層級使用 `Const`。 這表示變數的宣告*內容*必須是類別、結構、模組、程式或區塊，而且不能是原始程式檔、命名空間或介面。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 本機常數（在程式內）預設為公用存取，而且您不能在其上使用任何存取修飾詞。 類別和模組成員常數（在任何程式之外）預設為私用存取，而結構成員常數則預設為公用存取。 您可以使用存取修飾詞來調整其存取層級。  
  
## <a name="rules"></a>規則  
  
- **宣告內容。** 在任何程式以外的模組層級宣告的常數是*成員常數*;它是宣告它的類別、結構或模組的成員。  
  
     在程式層級宣告的常數是*本機常數*;它是在宣告它的程式或區塊的本機。  
  
- **特性.** 您只能將屬性套用至成員常數，而不能套用至本機常數。 屬性會將資訊提供給元件的中繼資料，這對暫存儲存體（例如本機常數）沒有意義。  
  
- **修改.** 根據預設，所有常數都是 `Shared`，`Static`，而 `ReadOnly`。 宣告常數時，您無法使用任何這些關鍵字。  
  
     在程式層級上，您無法使用 `Shadows` 或任何存取修飾詞來宣告本機常數。  
  
- **多個常數。** 您可以在同一個宣告語句中宣告數個常數，為每個常數指定 @no__t 0 部分。 以逗號分隔多個常數。  
  
## <a name="data-type-rules"></a>資料類型規則  
  
- **資料類型。** @No__t-0 語句可以宣告變數的資料類型。 您可以指定任何資料類型或列舉的名稱。  
  
- **預設類型。** 如果您未指定 `datatype`，常數會採用 `initializer` 的資料類型。 如果您同時指定 `datatype` 和 `initializer`，則 `initializer` 的資料類型必須可轉換為 `datatype`。 如果 `datatype` 或 `initializer` 都不存在，則資料類型會預設為 `Object`。  
  
- **不同的類型。** 您可以針對您所宣告的每個變數使用個別的 `As` 子句，為不同的常數指定不同的資料類型。 但是，您無法使用通用的 `As` 子句，將數個常數宣告為相同類型。  
  
- **初始.** 您必須初始化 `constantlist` 中每個常數的值。 您可以使用 `initializer` 來提供要指派給常數的運算式。 運算式可以是常值的任何組合、已定義的其他常數，以及已定義的列舉成員。 您可以使用算術和邏輯運算子來結合這類元素。  
  
     您不能在 `initializer` 中使用變數或函數。 不過，您可以使用轉換關鍵字（例如 `CByte` 和 `CShort`）。 如果您以常數 `String` 或 @no__t 2 引數呼叫它，您也可以使用 `AscW`，因為可以在編譯時期進行評估。  
  
## <a name="behavior"></a>行為  
  
- **範圍.** 本機常數只能從其程式或區塊記憶體取。 成員常數可從其類別、結構或模組內的任何位置存取。  
  
- **加.** 類別、結構或模組之外的程式碼必須使用該類別、結構或模組的名稱來限定成員常數的名稱。 程式或區塊外的程式碼無法參考該程式或區塊中的任何本機常數。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Const` 語句來宣告用來取代常值的常數。  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>範例  
 如果您定義了資料類型為 `Object` 的常數，Visual Basic 編譯器會提供 @no__t 的類型-1，而不是 `Object`。 在下列範例中，常數 `naturalLogBase` 的執行時間類型 `Decimal`。  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 上述範例會在[GetType 運算子](../../../visual-basic/language-reference/operators/gettype-operator.md)傳回的 <xref:System.Type> 物件上使用 <xref:System.Type.ToString%2A> 方法，因為 <xref:System.Type> 無法使用 `CStr` 轉換成 `String`。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)
- [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [常數和列舉](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [常數和列舉](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)

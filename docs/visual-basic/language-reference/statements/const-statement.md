---
title: Const 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 3d8134b43320003a6425cf284162d3d627b177c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623551"
---
# <a name="const-statement-visual-basic"></a>Const 陳述式 (Visual Basic)
宣告並定義一或多個常數。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>組件  
 `attributelist`  
 選擇性。 此陳述式中宣告的屬性套用至所有常數的清單。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)角括弧 ("`<`"和"`>`」)。  
  
 `accessmodifier`  
 選擇性。 使用此選項以指定哪些程式碼可以存取這些常數。 可以是[公開金鑰](../../../visual-basic/language-reference/modifiers/public.md)，[受保護](../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../visual-basic/language-reference/modifiers/friend.md)， [Protected Friend](../modifiers/protected-friend.md)，[私人](../../../visual-basic/language-reference/modifiers/private.md)，或  [Private Protected](../../language-reference/modifiers/private-protected.md)。
  
 `Shadows`  
 選擇性。 使用此選項，重新宣告並隱藏基底類別中的程式設計項目。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
 `constantlist`  
 必要項。 此陳述式所宣告的常數清單。  
  
 `constant` `[ ,` `constant` `... ]`  
  
 每個 `constant` 都具有下列語法和組件：  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|組件|描述|  
|----------|-----------------|  
|`constantname`|必要項。 常數的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`datatype`|需要`Option Strict`是`On`。 資料類型的常數。|  
|`initializer`|必要項。 在編譯時期評估，以及指派給常數的運算式。|  
  
## <a name="remarks"></a>備註  
 如果您將永遠不會變更值在您的應用程式時，您可以定義具名的常數，並使用它來取代常值的值。 值，比記住的工作變得更容易的名稱。 您可以一次定義常數，並使用它在許多地方，在您的程式碼。 如果您需要較新版本中重新定義的值，`Const`陳述式是唯一的地方，您需要進行變更。  
  
 您可以使用`Const`只能在模組或程序層級。 這表示*宣告內容*變數必須是類別、 結構、 模組、 程序或區塊，而且不能是原始程式檔、 命名空間或介面。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 （在程序） 內的區域常數預設公用存取，因此您無法在其上使用任何存取修飾詞。 類別和模組成員 （以外的任何程序） 的常數預設為私用存取，而結構成員常數預設為公用存取。 您可以調整它們的存取層級，使用存取修飾詞。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 常數的宣告是在模組層級以外的任何程序，而是*成員常數*; 它是成員的類別、 結構或模組，將其宣告。  
  
     在程序層級宣告的常數是*的區域常數*; 它是本機程序或將其宣告的區塊。  
  
-   **屬性。** 您可以將屬性套用到成員常數，而非區域常數。 屬性會提供資訊給組件的中繼資料，這不是暫時的儲存體，例如區域常數才有意義。  
  
-   **修飾詞。** 根據預設，所有的常數會`Shared`， `Static`，和`ReadOnly`。 宣告常數時，您無法使用這些關鍵字。  
  
     在程序層級，您無法使用`Shadows`或任何存取修飾詞來宣告區域常數。  
  
-   **多個常數。** 您可以宣告在相同的宣告陳述式中，數個常數指定`constantname`針對每個部分。 以逗號分隔多個常數。  
  
## <a name="data-type-rules"></a>資料型別規則  
  
-   **資料類型。** `Const`陳述式可以宣告一個變數的資料類型。 您可以指定任何資料類型或列舉型別名稱。  
  
-   **預設類型。** 如果您未指定`datatype`，常數會採用的資料型別`initializer`。 如果您同時指定`datatype`並`initializer`的資料類型`initializer`必須可轉換成`datatype`。 如果既未`datatype`也`initializer`已存在，將資料類型會預設為`Object`。  
  
-   **型別不同。** 您可以指定不同的常數的不同資料類型使用個別`As`子句宣告每個變數。 不過，您不能宣告為相同的型別使用通用的數個常數`As`子句。  
  
-   **初始化。** 您必須初始化中的每個常數值`constantlist`。 您使用`initializer`提供要指派給常數的運算式。 運算式可以是常值、 已定義，其他常數和列舉成員已定義的任何組合。 您可以使用算術和邏輯運算子來結合這類項目。  
  
     您無法使用變數或函式中的`initializer`。 不過，您可以使用轉換關鍵字這類`CByte`和`CShort`。 您也可以使用`AscW`如果您呼叫它具有常數`String`或`Char`引數，因為，可以在編譯時期評估。  
  
## <a name="behavior"></a>行為  
  
-   **範圍。** 區域常數是只能從其程序或區塊內存取。 成員的常數是可從其類別、 結構或模組內的任何地方存取。  
  
-   **限定性條件。** 程式碼類別之外，結構或模組必須限定成員常數的名稱，該類別、 結構或模組的名稱。 程式碼的外部程序或區塊不能參考該程序或區塊內的任何區域常數。  
  
## <a name="example"></a>範例  
 下列範例會使用`Const`陳述式來宣告常數，用來取代常值。  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a>範例  
 如果您定義資料類型的常數`Object`，Visual Basic 編譯器會產生它的型別`initializer`，而不是`Object`。 在下列範例中，常數`naturalLogBase`執行階段類型`Decimal`。  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 上述範例會使用<xref:System.Type.ToString%2A>方法<xref:System.Type>所傳回的物件[GetType 運算子](../../../visual-basic/language-reference/operators/gettype-operator.md)，因為<xref:System.Type>無法轉換成`String`使用`CStr`。  
  
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

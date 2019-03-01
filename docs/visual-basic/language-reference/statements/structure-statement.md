---
title: Structure 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: e8d312bc14cf4df3825586de0eba5cba64856268
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977509"
---
# <a name="structure-statement"></a>Structure 陳述式
宣告結構的名稱，並引進變數、 屬性、 事件和結構包含的程序的定義。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attributelist`|選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />- [為 protected 的 Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [受保護的私用](../../language-reference/modifiers/private-protected.md) <br /><br /> 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`Partial`|選擇性。 表示結構的部分定義。 請參閱[部分](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必要項。 此結構的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇性。 指定這為泛型結構。|  
|`typelist`|如果您使用所需[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。 此結構的型別參數的清單。 請參閱[輸入清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Implements`|選擇性。 指出此結構實作的一個或多個介面成員。 請參閱[實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果您使用所需`Implements`陳述式。 這個結構所實作的介面名稱。|  
|`datamemberdeclarations`|必要項。 零或多個`Const`， `Dim`， `Enum`，或`Event`陳述式宣告*資料成員*的結構。|  
|`methodmemberdeclarations`|選擇性。 零或多個宣告`Function`， `Operator`， `Property`，或`Sub`程序，做為*方法成員*的結構。|  
|`End Structure`|必要項。 終止`Structure`定義。|  
  
## <a name="remarks"></a>備註  
 `Structure`陳述式會定義您可以自訂的複合值類型。 A*結構*為一般化的使用者定義型別 (UDT) 的舊版的 Visual Basic。 如需詳細資訊，請參閱 <<c0> [ 結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)。  
  
 結構可支援許多與類別相同的功能。 比方說，結構可以具有屬性和程序，它們可以實作介面，並可以有參數化建構函式。 不過，有顯著的不同結構和類別繼承、 宣告和使用方式等方面。 此外，類別是參考型別，結構是實值型別。 如需詳細資訊，請參閱 <<c0> [ 結構和類別](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 您可以使用`Structure`只能在命名空間或模組層級。 這表示*宣告內容*結構必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，而且不可以是程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 結構的預設值為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以調整它們的存取層級，使用存取修飾詞。 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
-   **巢狀結構。** 您可以定義在另一個結構。 外部結構稱為*包含結構*，而內部結構稱為*巢狀結構*。 不過，您無法存取巢狀的結構的成員透過包含的結構。 相反地，您必須宣告巢狀的結構的資料類型的變數。  
  
-   **成員宣告。** 您必須宣告結構的每個成員。 結構成員不可[Protected](../../../visual-basic/language-reference/modifiers/protected.md)或`Protected Friend`因為不可以繼承結構。 結構本身，不過，可以是`Protected`或`Protected Friend`。  
  
     您可以在結構中宣告零個或多個非共用變數，或非共用、非自訂的事件。 您不能有常數、 屬性和程序，即使其中一些非共用。  
  
-   **初始化。** 您無法初始化其宣告結構的任何非共用的資料成員的值。 您必須透過參數化建構函式的結構，初始化資料成員或指派給成員的值之後您已建立結構的執行個體。  
  
-   **繼承**： 結構無法而非繼承自任何型別<xref:System.ValueType>，繼承的所有結構。 特別是，一個結構無法繼承自另一個。  
  
     您無法使用[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)在結構定義中，甚至指定<xref:System.ValueType>。  
  
-   **實作。** 如果使用結構[Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)，您必須實作由您指定在每個介面所定義的每個成員`interfacenames`。  
  
-   **預設屬性。** 結構可以指定最多一個屬性作為其*屬性預設*，並使用[預設](../../../visual-basic/language-reference/modifiers/default.md)修飾詞。 如需詳細資訊，請參閱 <<c0> [ 預設](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
-   **存取層級。** 在結構內，您可以宣告具有它自己的存取層級的每個成員。 所有的結構成員預設為[公開](../../../visual-basic/language-reference/modifiers/public.md)存取。 請注意，是否結構本身具有更具限制性的存取層級，這會自動限制存取其成員，即使您調整它們的存取層級，使用存取修飾詞。  
  
-   **範圍。** 結構是在其包含命名空間、 類別、 結構或模組的範圍中。  
  
     每個結構成員的範圍是整個結構。  
  
-   **存留期。** 結構本身沒有存留期。 相反地，該結構的每個執行個體都獨立於其他所有執行個體的存留期間。  
  
     執行個體的存留期開始時就會建立[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)子句。 保存之變數的存留期結束時結束。  
  
     您無法擴充的結構執行個體的存留期。 模組會提供靜態結構功能的近似值。 如需詳細資訊，請參閱 < [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     結構成員的存留期取決於它們所宣告的方式和位置。 如需詳細資訊，請參閱 「 存留期 」 中[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)。  
  
-   **限定性條件。** 結構之外的程式碼必須限定成員名稱，該結構的名稱。  
  
     如果巢狀結構內的程式碼進行程式設計的項目參考未限定，Visual Basic 搜尋項目第一次在巢狀結構中，然後在其包含的結構，等到最外層的包含項目。 如需詳細資訊，請參閱 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
-   **記憶體耗用量。** 如同所有的複合資料類型，您無法合併其成員的名義上的儲存體配置，安全地計算結構的總記憶體耗用量。 此外，您無法安全地假設在記憶體中的儲存體的順序是您宣告的順序相同。 如果您需要控制結構的儲存體配置，您可以申請<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性設定為`Structure`陳述式。  
  
## <a name="example"></a>範例  
 下列範例會使用`Structure`陳述式來定義一組相關資料的員工。 它示範如何使用`Public`， `Friend`，和`Private`成員，以反映的敏感性資料的項目。 它也會顯示程序、 屬性和事件的成員。  
  
 [!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>另請參閱
- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)
- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)
- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)
- [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [結構和類別](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)

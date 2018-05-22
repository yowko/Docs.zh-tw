---
title: Structure 陳述式
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
ms.openlocfilehash: 6fdc4f1d2fbd40689c76a15a5a35b25522138be6
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="structure-statement"></a>Structure 陳述式
宣告結構的名稱，並導入的變數、 屬性、 事件和結構包含的程序定義。  
  
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
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Protected 的 Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [受保護的私用](../../language-reference/modifiers/private-protected.md) <br /><br /> 請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`Partial`|選擇性。 指出此結構的部分定義。 請參閱[部分](../../../visual-basic/language-reference/modifiers/partial.md)。|  
|`name`|必要。 此結構的名稱。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇性。 指定這為泛型結構。|  
|`typelist`|如果您使用所需[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。 此結構的型別參數的清單。 請參閱[輸入清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Implements`|選擇性。 指出此結構實作一或多個介面的成員。 請參閱[實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果您使用所需`Implements`陳述式。 此結構實作的介面名稱。|  
|`datamemberdeclarations`|必要。 零或多個`Const`， `Dim`， `Enum`，或`Event`宣告陳述式*資料成員*的結構。|  
|`methodmemberdeclarations`|選擇性。 零或多個宣告的`Function`， `Operator`， `Property`，或`Sub`程序，做為*方法成員*的結構。|  
|`End Structure`|必要。 終止`Structure`定義。|  
  
## <a name="remarks"></a>備註  
 `Structure`陳述式會定義您可以自訂複合的實值型別。 A*結構*為一般化的使用者定義型別 (UDT) 的先前版本的 Visual Basic。 如需詳細資訊，請參閱[結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)。  
  
 結構可以支援許多與類別相同的功能。 例如，結構還可以具有屬性和程序、 可以實作介面，和可以有參數化建構函式。 不過，有明顯差異結構和類別方面，例如繼承的宣告和使用方式。 此外，類別是參考類型和結構是實值類型。 如需詳細資訊，請參閱[結構和類別](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 您可以使用`Structure`只能在命名空間或模組層級。 這表示*宣告內容*結構必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，並且不能是程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 結構會預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以調整其存取層級，使用存取修飾詞。 如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
-   **巢狀結構。** 您可以定義在另一個結構。 外部結構稱為*包含結構*，而內部結構稱為*巢狀結構*。 不過，您無法透過包含的結構來存取巢狀的結構的成員。 相反地，您必須宣告巢狀的結構的資料類型的變數。  
  
-   **成員宣告。** 您必須宣告結構的每個成員。 結構成員無法[保護](../../../visual-basic/language-reference/modifiers/protected.md)或`Protected Friend`因為不可以是繼承自結構。 結構本身，不過，可以是`Protected`或`Protected Friend`。  
  
     您可以在結構中宣告零個或多個非共用變數，或非共用、非自訂的事件。 您不能有常數、 屬性和程序，即使其中一些會共用。  
  
-   **初始化。** 您無法初始化結構中宣告的任何非共用的資料成員的值。 您必須在結構上的參數化建構函式來初始化資料成員，或建立結構的執行個體之後，指派給成員值。  
  
-   **繼承**： 結構無法不是繼承自任何型別<xref:System.ValueType>，從其所有的結構會繼承。 特別是，一個結構無法繼承自另一個。  
  
     您無法使用[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)在結構定義中，即使指定<xref:System.ValueType>。  
  
-   **實作。** 如果結構使用[Implements 陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)，您必須實作由您指定在每個介面所定義的每個成員`interfacenames`。  
  
-   **預設屬性。** 結構可以指定最多一個屬性做為其*預設屬性*，並使用[預設](../../../visual-basic/language-reference/modifiers/default.md)修飾詞。 如需詳細資訊，請參閱[預設](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
-   **存取層級。** 在結構內，您可以宣告具有自己的存取層級的每個成員。 所有的結構成員預設為[公用](../../../visual-basic/language-reference/modifiers/public.md)存取。 請注意，如果結構本身會有更多限制的存取層級，會自動限制存取其成員，即使您調整其存取層級，使用存取修飾詞。  
  
-   **範圍。** 結構是在範圍中，其包含命名空間、 類別、 結構或模組。  
  
     每個結構成員的範圍是整個結構。  
  
-   **存留期。** 結構本身沒有的存留期。 相反地，每個執行個體，該結構有獨立的所有其他執行個體的存留期。  
  
     執行個體的存留期開始時就會建立[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md)子句。 它會結束保存之變數的存留期結束時。  
  
     您無法延伸結構執行個體的存留期。 模組會提供靜態結構功能的近似值。 如需詳細資訊，請參閱[Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)。  
  
     結構成員的存留期取決於它們所宣告的方式和位置。 如需詳細資訊，請參閱 「 存留時間 」 中[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)。  
  
-   **限定性條件。** 結構之外的程式碼必須限定成員名稱，與該結構的名稱。  
  
     如果巢狀結構內的程式碼會不合格的程式設計項目參考，Visual Basic 會搜尋項目的第一次在巢狀結構中，然後在其包含的結構，依此類推最外層包含的項目。 如需詳細資訊，請參閱[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
-   **記憶體耗用量。** 如同所有的複合資料類型，您無法安全地將相加名義儲存配置，其成員的計算結構的總記憶體耗用量。 此外，您不能安全地假設在記憶體中的儲存體的順序是您宣告的順序相同。 如果您需要控制結構的儲存體配置，您可以套用<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性`Structure`陳述式。  
  
## <a name="example"></a>範例  
 下列範例會使用`Structure`陳述式來定義一組相關資料的員工。 它示範如何使用`Public`， `Friend`，和`Private`成員，以反映資料項目的敏感度。 它也會顯示程序、 屬性和事件的成員。  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [結構和類別](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)

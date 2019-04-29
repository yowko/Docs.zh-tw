---
title: Interface 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: db39759a804905450e7f8913f45e8ddab39d8416
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784185"
---
# <a name="interface-statement-visual-basic"></a>Interface 陳述式 (Visual Basic)
宣告介面的名稱，並引進組成介面成員的定義。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`attributelist`|選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私用](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [為 protected 的 Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [受保護的私用](../../language-reference/modifiers/private-protected.md)<br /><br /> 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`name`|必要項。 這個介面的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇性。 指定這為泛型介面。|  
|`typelist`|如果您使用所需[的](../../../visual-basic/language-reference/statements/of-clause.md)關鍵字。 此介面的型別參數的清單。 （選擇性） 每個類型參數可以宣告 variant 利用`In`和`Out`泛型修飾詞。 請參閱[輸入清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇性。 指出此介面繼承的屬性和另一個介面或介面的成員。 請參閱[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`interfacenames`|如果您使用所需`Inherits`陳述式。 從這個介面衍生的介面名稱。|  
|`modifiers`|選擇性。 適當的修飾詞所定義的介面成員。|  
|`Property`|選擇性。 定義介面成員的屬性。|  
|`Function`|選擇性。 定義`Function`是介面成員的程序。|  
|`Sub`|選擇性。 定義`Sub`是介面成員的程序。|  
|`Event`|選擇性。 定義事件介面的成員。|  
|`Interface`|選擇性。 定義此介面內的巢狀的介面。 巢狀的介面定義必須終止使用`End Interface`陳述式。|  
|`Class`|選擇性。 定義的介面成員的類別。 成員類別定義必須終止使用`End Class`陳述式。|  
|`Structure`|選擇性。 定義介面成員的結構。 成員結構定義必須終止使用`End Structure`陳述式。|  
|`membername`|所需的每個屬性、 程序、 事件、 介面、 類別或結構定義為介面的成員。 成員的名稱。|  
|`End Interface`|終止`Interface`定義。|  
  
## <a name="remarks"></a>備註  
 *介面*定義一組成員，例如屬性和程序的類別和結構可以實作。 介面定義的成員和非內部運作的簽章。  
  
 類別或結構實作介面所提供的介面所定義的每個成員的程式碼。 最後，當應用程式從該類別或結構中建立執行個體，物件存在，而且會在記憶體中執行。 如需詳細資訊，請參閱 <<c0> [ 物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)並[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 您可以使用`Interface`只能在命名空間或模組層級。 這表示*宣告內容*介面必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，而且不可以是程序或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 介面會預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以調整它們的存取層級，使用存取修飾詞。 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
- **巢狀介面。** 您可以定義一個介面，在另一個。 外部介面稱為*包含介面*，而內部介面稱為*巢狀的介面*。  
  
- **成員宣告。** 當您為介面成員宣告的屬性或程序時，您會定義只*簽章*的該屬性或程序。 這包括項目類型 （屬性或程序），其參數和參數類型，以及其傳回型別。 因為這個緣故，成員定義使用只有一行程式碼，以及終止陳述式，例如`End Function`或`End Property`介面中不正確。  
  
     相反地，當您定義列舉型別或結構，或巢狀的類別或介面，就必須包含其資料成員。  
  
- **成員修飾詞。** 定義模組的成員時，您無法使用任何存取修飾詞，也不能指定[Shared](../../../visual-basic/language-reference/modifiers/shared.md)或任何程序修飾詞，除了[多載](../../../visual-basic/language-reference/modifiers/overloads.md)。 您可以宣告任何成員都具有[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)，而且您可以使用[預設](../../../visual-basic/language-reference/modifiers/default.md)定義屬性時，以及[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)或[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。  
  
- **繼承**： 如果此介面使用[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)，您可以指定一或多個基底介面。 您可以繼承自兩個介面，即使它們都各自定義具有相同名稱的成員。 如果您這樣做時，實作程式碼必須使用名稱限定性條件來指定它所實作的成員。  
  
     介面無法繼承自另一個介面具有更嚴格的存取層級。 例如，`Public`介面無法繼承自`Friend`介面。  
  
     介面無法繼承自的巢狀介面。  
  
- **實作。** 當類別會使用[實作](../../../visual-basic/language-reference/statements/implements-clause.md)陳述式來實作這個介面，它必須實作在介面中定義的每個成員。 此外，實作程式碼中的每個簽章必須完全符合對應的簽章，此介面中所定義。 不過，實作程式碼中的成員名稱不必符合介面中定義的成員名稱。  
  
     當類別實作的程序時，它不能指定為程序`Shared`。  
  
- **預設屬性。** 介面可以指定最多一個屬性作為其*屬性預設*，它可以參考而不使用屬性名稱。 您藉由宣告它與指定這類屬性[預設](../../../visual-basic/language-reference/modifiers/default.md)修飾詞。  
  
     請注意，這表示只有當未繼承介面可以定義預設屬性。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 所有介面成員以隱含方式都具有[公開](../../../visual-basic/language-reference/modifiers/public.md)存取。 定義成員時，您無法使用任何存取修飾詞。 不過，實作介面的類別可以宣告存取層級的每個實作的成員。  
  
     如果您將類別執行個體指派給變數時，其成員的存取層級取決於該變數的資料型別是否基礎介面實作的類別。 下列範例將說明這點。  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     如果您在存取類別成員透過`varAsInterface`，它們都有公用存取。 不過，如果您在存取透過成員`varAsClass`，則`Sub`程序`doSomething`具有私用存取。  
  
- **範圍。** 介面是在整個命名空間、 類別、 結構或模組的範圍內。  
  
     每個介面成員的範圍是整個的介面。  
  
- **存留期。** 介面本身不會有存留期，也不會影響其成員。 當類別實作介面及物件會建立為執行個體的類別，物件具有存留期內正在執行的應用程式。 如需詳細資訊，請參閱 「 存留期 」 中[Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)。  
  
## <a name="example"></a>範例  
 下列範例會使用`Interface`陳述式來定義名為的介面`thisInterface`，它必須用來實作`Property`陳述式和`Function`陳述式。  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 請注意，`Property`並`Function`陳述式不會導入區塊結尾`End Property`和`End Function`在介面中。 介面會定義只其成員的簽章。 完整`Property`並`Function`區塊會出現在類別若實作`thisInterface`。  
  
## <a name="see-also"></a>另請參閱

- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)
- [Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [泛型介面中的變異數](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

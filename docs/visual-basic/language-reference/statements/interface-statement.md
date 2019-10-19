---
title: Interface 陳述式 (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 68590702835e47e5f0f2e0380bc0fe4017d5eb15
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582675"
---
# <a name="interface-statement-visual-basic"></a>Interface 陳述式 (Visual Basic)
宣告介面的名稱，並引進介面所組成的成員定義。  
  
## <a name="syntax"></a>語法  
  
```vb  
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
|`attributelist`|選擇項。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。|  
|`accessmodifier`|選擇項。 可以是下列其中一項：<br /><br /> -   [公用](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [保護](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [私](../../../visual-basic/language-reference/modifiers/private.md)用<br />-  [受保護的 Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [私用保護](../../language-reference/modifiers/private-protected.md)<br /><br /> 請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。 請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`name`|必要項。 此介面的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇項。 指定這是泛型介面。|  
|`typelist`|如果您使用 of 關鍵字，則[為必要項](../../../visual-basic/language-reference/statements/of-clause.md)。 此介面的型別參數清單。 或者，您可以使用 `In` 和 `Out` 泛型修飾詞，將每個型別參數宣告為 variant。 請參閱[類型清單](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇項。 指出此介面會繼承另一個介面或介面的屬性和成員。 請參閱[Inherits 語句](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`interfacenames`|如果您使用 `Inherits` 語句，則為必要。 這個介面衍生自的介面名稱。|  
|`modifiers`|選擇項。 定義之介面成員的適當修飾詞。|  
|`Property`|選擇項。 定義屬於介面成員的屬性。|  
|`Function`|選擇項。 定義屬於介面成員的 `Function` 程式。|  
|`Sub`|選擇項。 定義屬於介面成員的 `Sub` 程式。|  
|`Event`|選擇項。 定義屬於介面成員的事件。|  
|`Interface`|選擇項。 定義在此介面內嵌套的介面。 嵌套介面定義必須以 `End Interface` 語句終止。|  
|`Class`|選擇項。 定義屬於介面成員的類別。 成員類別定義必須以 `End Class` 語句終止。|  
|`Structure`|選擇項。 定義屬於介面成員的結構。 成員結構定義必須以 `End Structure` 語句終止。|  
|`membername`|定義為介面成員的每個屬性、程式、事件、介面、類別或結構都是必要專案。 成員的名稱。|  
|`End Interface`|終止 `Interface` 定義。|  
  
## <a name="remarks"></a>備註  
 *介面*會定義類別和結構可以實作為的一組成員，例如屬性和程式。 介面只會定義成員的簽章，而不是其內部工作的簽章。  
  
 類別或結構會藉由提供介面所定義之每個成員的程式碼，來實作為介面。 最後，當應用程式從該類別或結構建立實例時，物件存在並在記憶體中執行。 如需詳細資訊，請參閱[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)和[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 您只能在命名空間或模組層級使用 `Interface`。 這表示介面的宣告*內容*必須是原始程式檔、命名空間、類別、結構、模組或介面，而且不能是程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 介面預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以使用存取修飾詞來調整其存取層級。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
- **嵌套介面。** 您可以在另一個中定義一個介面。 外部介面稱為*包含介面*，而內部介面稱為「*嵌套介面*」。  
  
- **成員宣告。** 當您將屬性或程式宣告為介面的成員時，您只會*定義該屬性或程式的簽*章。 這包括元素類型（屬性或程式）、其參數和參數類型，以及其傳回類型。 因此，成員定義只會使用一行程式碼，而 `End Function` 或 `End Property` 之類的終止語句在介面中是不正確。  
  
     相反地，當您定義列舉或結構或是嵌套類別或介面時，必須包含其資料成員。  
  
- **成員修飾詞。** 您不能在定義模組成員時使用任何存取修飾詞，也不能指定[共用](../../../visual-basic/language-reference/modifiers/shared.md)或任何程式修飾詞，但多[載除外。](../../../visual-basic/language-reference/modifiers/overloads.md) 您可以使用[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)宣告任何成員，而且可以在定義屬性時使用[預設值](../../../visual-basic/language-reference/modifiers/default.md)，以及[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)或[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。  
  
- **繼承**： 如果介面使用[Inherits 語句](../../../visual-basic/language-reference/statements/inherits-statement.md)，您可以指定一或多個基底介面。 您可以從兩個介面繼承，即使它們各自訂具有相同名稱的成員。 如果您這樣做，則執行程式碼必須使用名稱限定性來指定它所要執行的成員。  
  
     介面無法繼承自具有更嚴格存取層級的另一個介面。 例如，`Public` 介面無法繼承自 `Friend` 介面。  
  
     介面無法繼承自其內所嵌套的介面。  
  
- **實作.** 當類別使用[Implements](../../../visual-basic/language-reference/statements/implements-clause.md)語句來執行此介面時，它必須執行介面中定義的每個成員。 此外，執行程式碼中的每個簽章都必須完全符合此介面中定義的對應簽章。 不過，執行程式碼中的成員名稱不需要符合介面中定義的成員名稱。  
  
     當類別正在執行程式時，它無法將程式指定為 `Shared`。  
  
- **Default 屬性。** 介面最多可以指定一個屬性做為其*預設屬性*，而不需要使用屬性名稱即可加以參考。 您可以使用[預設](../../../visual-basic/language-reference/modifiers/default.md)的修飾詞來宣告這類屬性，以指定此屬性。  
  
     請注意，這表示介面只有在繼承 none 時，才可以定義預設屬性。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 所有介面成員都隱含具有[公用](../../../visual-basic/language-reference/modifiers/public.md)存取權。 定義成員時，您無法使用任何存取修飾詞。 不過，執行介面的類別可以宣告每個已實成員的存取層級。  
  
     如果您將類別實例指派給變數，其成員的存取層級可能取決於變數的資料類型為基礎介面或實作為類別。 下列範例將說明這點。  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     如果您透過 `varAsInterface` 存取類別成員，則它們都具有公用存取權。 不過，如果您透過 `varAsClass` 存取成員，則 `Sub` 程式 `doSomething` 具有私用存取權。  
  
- **範圍.** 介面會在其命名空間、類別、結構或模組的範圍內。  
  
     每個介面成員的範圍都是整個介面。  
  
- **期.** 介面本身不具有存留期，也不會有其成員。 當類別執行介面，並將物件建立為該類別的實例時，物件在其執行所在的應用程式內會有存留期。 如需詳細資訊，請參閱[Class 語句](../../../visual-basic/language-reference/statements/class-statement.md)中的「存留期」。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Interface` 語句來定義名為 `thisInterface` 的介面，它必須使用 `Property` 語句和 `Function` 語句來執行。  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 請注意，`Property` 和 `Function` 語句不會在介面中引進以 `End Property` 和 `End Function` 結尾的區塊。 介面只會定義其成員的簽章。 完整的 `Property` 和 `Function` 區塊會出現在執行 `thisInterface` 的類別中。  
  
## <a name="see-also"></a>請參閱

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

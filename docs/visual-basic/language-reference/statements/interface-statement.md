---
title: Interface 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 02d258084aaaa53dcc559cfaa0dec27556351037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404482"
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
|`attributelist`|選擇性。 請參閱[屬性清單](attribute-list.md)。|  
|`accessmodifier`|選擇性。 可以是下列其中一項：<br /><br /> -   [公立](../modifiers/public.md)<br />-   [免受](../modifiers/protected.md)<br />-   [給](../modifiers/friend.md)<br />-   [私人](../modifiers/private.md)<br />-  [受保護的 Friend](../modifiers/protected-friend.md)<br/>- [私用保護](../modifiers/private-protected.md)<br /><br /> 請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇性。 請參閱[Shadows](../modifiers/shadows.md)。|  
|`name`|必要。 此介面的名稱。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`Of`|選擇性。 指定這是泛型介面。|  
|`typelist`|如果您使用 of 關鍵字，則[為必要項](of-clause.md)。 此介面的型別參數清單。 您可以選擇性地使用和泛型修飾詞，將每個類型參數宣告為 variant `In` `Out` 。 請參閱[類型清單](type-list.md)。|  
|`Inherits`|選擇性。 指出此介面會繼承另一個介面或介面的屬性和成員。 請參閱[Inherits 語句](inherits-statement.md)。|  
|`interfacenames`|如果您使用語句，則為必要 `Inherits` 。 這個介面衍生自的介面名稱。|  
|`modifiers`|選擇性。 定義之介面成員的適當修飾詞。|  
|`Property`|選擇性。 定義屬於介面成員的屬性。|  
|`Function`|選擇性。 定義 `Function` 屬於介面成員的程式。|  
|`Sub`|選擇性。 定義 `Sub` 屬於介面成員的程式。|  
|`Event`|選擇性。 定義屬於介面成員的事件。|  
|`Interface`|選擇性。 定義在此介面內嵌套的介面。 此嵌套介面定義必須以語句終止 `End Interface` 。|  
|`Class`|選擇性。 定義屬於介面成員的類別。 成員類別定義必須以 `End Class` 語句終止。|  
|`Structure`|選擇性。 定義屬於介面成員的結構。 成員結構定義必須以 `End Structure` 語句終止。|  
|`membername`|定義為介面成員的每個屬性、程式、事件、介面、類別或結構都是必要專案。 成員的名稱。|  
|`End Interface`|結束 `Interface` 定義。|  
  
## <a name="remarks"></a>備註  
 *介面*會定義類別和結構可以實作為的一組成員，例如屬性和程式。 介面只會定義成員的簽章，而不是其內部工作的簽章。  
  
 類別或結構會藉由提供介面所定義之每個成員的程式碼，來實作為介面。 最後，當應用程式從該類別或結構建立實例時，物件存在並在記憶體中執行。 如需詳細資訊，請參閱[物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)和[介面](../../programming-guide/language-features/interfaces/index.md)。  
  
 您 `Interface` 只能在命名空間或模組層級使用。 這表示介面的宣告*內容*必須是原始程式檔、命名空間、類別、結構、模組或介面，而且不能是程式或區塊。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。  
  
 介面預設為[Friend](../modifiers/friend.md)存取。 您可以使用存取修飾詞來調整其存取層級。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
- **嵌套介面。** 您可以在另一個中定義一個介面。 外部介面稱為*包含介面*，而內部介面稱為「*嵌套介面*」。  
  
- **成員宣告。** 當您將屬性或程式宣告為介面的成員時，您只會*定義該屬性或程式的簽*章。 這包括元素類型（屬性或程式）、其參數和參數類型，以及其傳回類型。 因此，成員定義只會使用一行程式碼，而在介面中終止語句（例如 `End Function` 或） `End Property` 是不正確。  
  
     相反地，當您定義列舉或結構或是嵌套類別或介面時，必須包含其資料成員。  
  
- **成員修飾詞。** 您不能在定義模組成員時使用任何存取修飾詞，也不能指定[共用](../modifiers/shared.md)或任何程式修飾詞，但多[載除外。](../modifiers/overloads.md) 您可以使用[Shadows](../modifiers/shadows.md)宣告任何成員，而且可以在定義屬性時使用[預設值](../modifiers/default.md)，以及[ReadOnly](../modifiers/readonly.md)或[WriteOnly](../modifiers/writeonly.md)。  
  
- **繼承性.** 如果介面使用[Inherits 語句](inherits-statement.md)，您可以指定一或多個基底介面。 您可以從兩個介面繼承，即使它們各自訂具有相同名稱的成員。 如果您這樣做，則執行程式碼必須使用名稱限定性來指定它所要執行的成員。  
  
     介面無法繼承自具有更嚴格存取層級的另一個介面。 例如， `Public` 介面無法繼承自 `Friend` 介面。  
  
     介面無法繼承自其內所嵌套的介面。  
  
- **實作.** 當類別使用[Implements](implements-clause.md)語句來執行此介面時，它必須執行介面中定義的每個成員。 此外，執行程式碼中的每個簽章都必須完全符合此介面中定義的對應簽章。 不過，執行程式碼中的成員名稱不需要符合介面中定義的成員名稱。  
  
     當類別正在執行程式時，它無法將程式指定為 `Shared` 。  
  
- **Default 屬性。** 介面最多可以指定一個屬性做為其*預設屬性*，而不需要使用屬性名稱即可加以參考。 您可以使用[預設](../modifiers/default.md)的修飾詞來宣告這類屬性，以指定此屬性。  
  
     請注意，這表示介面只有在繼承 none 時，才可以定義預設屬性。  
  
## <a name="behavior"></a>行為  
  
- **存取層級。** 所有介面成員都隱含具有[公用](../modifiers/public.md)存取權。 定義成員時，您無法使用任何存取修飾詞。 不過，執行介面的類別可以宣告每個已實成員的存取層級。  
  
     如果您將類別實例指派給變數，其成員的存取層級可能取決於變數的資料類型為基礎介面或實作為類別。 下列範例將說明這點。  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     如果您透過存取類別成員 `varAsInterface` ，則它們都具有公用存取權。 不過，如果您透過存取成員 `varAsClass` ，則此程式 `Sub` `doSomething` 具有私用存取權。  
  
- **範圍.** 介面會在其命名空間、類別、結構或模組的範圍內。  
  
     每個介面成員的範圍都是整個介面。  
  
- **期.** 介面本身不具有存留期，也不會有其成員。 當類別執行介面，並將物件建立為該類別的實例時，物件在其執行所在的應用程式內會有存留期。 如需詳細資訊，請參閱[Class 語句](class-statement.md)中的「存留期」。  
  
## <a name="example"></a>範例  
 下列範例 `Interface` 會使用語句來定義名為的介面 `thisInterface` ，它必須使用 `Property` 語句和語句來執行 `Function` 。  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 請注意， `Property` 和 `Function` 語句不會在介面中引進以和結尾的區塊 `End Property` `End Function` 。 介面只會定義其成員的簽章。 完整 `Property` 和 `Function` 區塊會出現在所執行的類別中 `thisInterface` 。  
  
## <a name="see-also"></a>另請參閱

- [介面](../../programming-guide/language-features/interfaces/index.md)
- [Class 陳述式](class-statement.md)
- [Module 陳述式](module-statement.md)
- [Structure 陳述式](structure-statement.md)
- [Property Statement](property-statement.md)
- [Function 陳述式](function-statement.md)
- [Sub 陳述式](sub-statement.md)
- [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [泛型介面中的變異數](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [位於](../modifiers/in-generic-modifier.md)
- [脫銷](../modifiers/out-generic-modifier.md)

---
title: Module 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 5628224a08fe5f12cf2a81b179c4998001174354
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779867"
---
# <a name="module-statement"></a>Module 陳述式
宣告模組的名稱，並引進變數、 屬性、 事件和組成模組的程序的定義。  
  
## <a name="syntax"></a>語法  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>組件  
 `attributelist`  
 選擇性。 請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
 `accessmodifier`  
 選擇性。 可以是下列其中一項：  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 `name`  
 必要。 此模組的名稱。 請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
 `statements`  
 選擇性。 定義的變數、 屬性、 事件、 程序和巢狀型別，此模組的陳述式。  
  
 `End Module`  
 終止`Module`定義。  
  
## <a name="remarks"></a>備註  
 A`Module`陳述式會定義可在其命名空間的參考型別。 A*模組*(有時也稱為*標準模組*) 類似的類別，但有一些重要的差別。 每個模組都有一個執行個體，並不需要建立或指派給變數。 模組不支援繼承或實作介面。 請注意，模組不是*型別*意思是類別或結構，您不能宣告為具有模組的資料類型的程式設計項目。  
  
 您可以使用`Module`只能在命名空間層級。 這表示*宣告內容*的模組必須是原始程式檔或命名空間，而且不得類別、 結構、 模組、 介面、 程序或區塊。 您無法巢狀在另一個模組，或任何類型內的模組。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 模組具有相同的存留期，為您的程式。 因為它的成員全部都`Shared`，它們也有相同的程式的存留期。  
  
 模組預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以調整它們的存取層級，使用存取修飾詞。 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 模組的所有成員都是隱含`Shared`。  
  
## <a name="classes-and-modules"></a>類別和模組  
 這些項目有許多相似之處，但有一些重要的差異。  
  
-   **術語。** 舊版的 Visual Basic 會辨識兩種模組類型：*類別的模組*（.cls 檔案） 和*標準模組*（.bas 檔案）。 目前的版本會呼叫這些*類別*並*模組*分別。  
  
-   **共用的成員。** 您可以控制類別的成員是否共用，或執行個體成員。  
  
-   **物件導向。** 類別是物件導向，但模組不是。 因此唯一的類別可以具現化為物件。 如需詳細資訊，請參閱 <<c0> [ 物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="rules"></a>規則  
  
-   **修飾詞。** 模組的所有成員都是隱含[共用](../../../visual-basic/language-reference/modifiers/shared.md)。 您無法使用`Shared`關鍵字宣告成員，而且您無法改變任何成員的共用的狀態。  
  
-   **繼承**： 模組無法而非繼承自任何型別<xref:System.Object>，繼承的所有模組。 特別是，一個模組無法繼承自另一個。  
  
     您無法使用[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)在模組定義中，甚至指定<xref:System.Object>。  
  
-   **預設屬性。** 您無法在模組中定義任何預設屬性。 如需詳細資訊，請參閱 <<c0> [ 預設](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
-   **存取層級。** 在模組內，您可以宣告具有它自己的存取層級的每個成員。 模組成員預設為[公開金鑰](../../../visual-basic/language-reference/modifiers/public.md)變數和常數，除了存取哪些預設[私人](../../../visual-basic/language-reference/modifiers/private.md)存取。 當模組有限制存取比多個成員時，指定的模組的存取層級的優先順序較高。  
  
-   **範圍。** 模組是在其命名空間的範圍中。  
  
     每個模組成員的範圍是整個模組。 請注意，所有成員都進行*類型提升*，因而導致其升級為包含模組的命名空間的範圍。 如需詳細資訊，請參閱 <<c0> [ 型別提升](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)。  
  
-   **限定性條件。** 您可以在專案中，有多個模組，您可以宣告具有相同名稱在兩個或多個模組中的成員。 不過，您必須限定這類成員的適當的模組名稱的任何參考，如果參考是從該模組外。 如需詳細資訊，請參閱 < [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Namespace 陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [型別提升](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)

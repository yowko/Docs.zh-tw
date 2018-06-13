---
title: Module 陳述式
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
ms.openlocfilehash: f4a0c7b772417085718b63569e8368178e348567
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605013"
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
 選擇性。 定義的變數、 屬性、 事件、 程序和此模組的巢狀的類型的陳述式。  
  
 `End Module`  
 終止`Module`定義。  
  
## <a name="remarks"></a>備註  
 A`Module`陳述式會定義可在整個其命名空間的參考類型。 A*模組*(有時稱為*標準模組*) 是類似類別，但有一些重要的區別。 每個模組都有一個執行個體，並不需要建立或指派給變數。 模組不支援繼承或實作介面。 請注意，模組是不*類型*類別或結構會在概念上，您無法宣告為具有模組的資料類型的程式設計項目。  
  
 您可以使用`Module`只能在命名空間層級。 這表示*宣告內容*模組必須是原始程式檔或命名空間，且不可為類別、 結構、 模組、 介面、 程序或區塊。 您無法巢狀模組內任何類型或另一個模組，內。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 模組都有相同的存留期為您的程式。 因為所有其成員，所以`Shared`，他們也擁有相同的程式的存留期。  
  
 模組預設為[Friend](../../../visual-basic/language-reference/modifiers/friend.md)存取。 您可以調整其存取層級，使用存取修飾詞。 如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 模組的所有成員都會隱含地`Shared`。  
  
## <a name="classes-and-modules"></a>類別和模組  
 這些項目有許多相似處，但有一些重要的差異。  
  
-   **術語。** 舊版的 Visual Basic 辨識兩種類型的模組：*類別模組*（.cls 檔案） 和*標準模組*（.bas 檔案）。 目前的版本會呼叫這些*類別*和*模組*分別。  
  
-   **共用的成員。** 您可以控制類別的成員是共用或執行個體成員。  
  
-   **物件的方向。** 類別是物件導向，但模組不是。 為物件，因此唯一類別可以具現化。 如需詳細資訊，請參閱[物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)。  
  
## <a name="rules"></a>規則  
  
-   **修飾詞。** 所有的模組成員會隱含地[共用](../../../visual-basic/language-reference/modifiers/shared.md)。 您無法使用`Shared`關鍵字宣告成員，而且您無法改變任何成員的共用的狀態時。  
  
-   **繼承**： 模組無法從任何型別繼承以外<xref:System.Object>，繼承的所有模組。 特別是，一個模組，無法繼承自另一個。  
  
     您無法使用[Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)在模組定義中，即使指定<xref:System.Object>。  
  
-   **預設屬性。** 您無法在模組中定義的任何預設屬性。 如需詳細資訊，請參閱[預設](../../../visual-basic/language-reference/modifiers/default.md)。  
  
## <a name="behavior"></a>行為  
  
-   **存取層級。** 在模組內，您可以宣告具有自己的存取層級的每個成員。 模組成員預設為[公用](../../../visual-basic/language-reference/modifiers/public.md)變數和常數，除了存取的預設值為[私人](../../../visual-basic/language-reference/modifiers/private.md)存取。 模組具有限制存取比多其中一個成員，指定的模組的存取層級會優先使用。  
  
-   **範圍。** 模組是在範圍中的命名空間。  
  
     每個模組成員的範圍是整個模組。 請注意，所有成員都接受*輸入促銷*，因而導致其升級為包含模組的命名空間範圍。 如需詳細資訊，請參閱[型別提升](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)。  
  
-   **限定性條件。** 您可以在專案中，有多個模組，您可以宣告具有相同名稱在兩個或多個模組中的成員。 不過，您必須限定這類成員具有適當的模組名稱的任何參考，如果參考是從該模組的外部。 如需詳細資訊，請參閱[宣告之項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Namespace 陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [型別提升](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)

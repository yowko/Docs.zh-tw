---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 81118b9e97f320bffdbb58e5e1a2859052c4cee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)
指定屬性或程序會覆寫繼承自基底類別的同名屬性或程序。  
  
## <a name="remarks"></a>備註  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您只能在屬性或程序宣告陳述式中使用 `Overrides`。  
  
-   **結合的修飾詞。** 您不能相同的宣告中同時指定 `Overrides` 與 `Shadows` 或 `Shared`。 因為覆寫項目可隱含覆寫，您無法結合 `Overridable` 與 `Overrides`。  
  
-   **相符簽章。** 此宣告的簽章必須完全符合*簽章*屬性或程序，它會覆寫。 這表示的參數清單必須有相同數目的參數、相同的順序及相同的資料類型。  
  
     除了簽章，覆寫宣告也必須完全符合下列各項：  
  
    -   存取層級  
  
    -   傳回型別 (如果有的話)  
  
-   **泛型簽章。** 在泛型程序中，簽章包含型別參數的個數。 因此，覆寫宣告在這方面也必須符合基底類別版本。  
  
-   **其他符合。** 除了符合簽章的基底類別版本，此宣告在下列方面也必須符合它：  
  
    -   存取層級修飾詞 (例如[公用](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   傳遞機制，每個參數 ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   泛型程序的每個型別參數的條件約束清單  
  
-   **遮蔽和覆寫。** 遮蔽和覆寫都會重新定義繼承的項目，但這兩種方法之間有顯著的差異。 如需詳細資訊，請參閱[Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
 如果您使用 `Overrides`，編譯器會隱含地新增 `Overloads`，讓程式庫 API 更容易使用 C#。  
  
 `Overrides` 修飾詞可用於以下內容：  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Visual Basic 中的泛型型別](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [類型清單](../../../visual-basic/language-reference/statements/type-list.md)

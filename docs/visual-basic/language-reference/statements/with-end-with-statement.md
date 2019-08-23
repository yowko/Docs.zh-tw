---
title: With...End With 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 3d26932c23299c6fbcb53b1389abd7694f529eef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963322"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With 陳述式 (Visual Basic)
執行一系列重複參考單一物件或結構的陳述式，使陳述式在存取物件或結構的成員時，可以使用簡化的語法。  使用結構時，您可以只讀取成員的值或叫用方法，如果嘗試指派值給 `With...End With` 陳述式中使用的結構成員，將會收到錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`objectExpression`|必要項。 判斷值為物件的運算式。 運算式可能會很複雜，而且只會評估一次。 運算式可以判斷值為任何資料類型，包括基礎類型。|  
|`statements`|選擇性。 在 `With` 和 `End With` 之間的一個或多個陳述式，這些陳述式可能會參考由 `objectExpression` 的評估所產生之物件的成員。|  
|`End With`|必要項。 終止 `With` 區塊的定義。|  
  
## <a name="remarks"></a>備註  
 您可以使用 `With...End With` 在指定的物件上執行一系列的陳述式，而不需多次指定物件的名稱。 在 `With` 陳述式區塊內，您可以指定以句號為開頭的物件成員，就如同 `With` 陳述式物件在其前方。  
  
 例如，若要變更單一物件的多個屬性，請將屬性指派陳述式置入 `With...End With` 區塊中，如此您只需參考該物件名稱一次，而不必在每次指派屬性時都要參考。  
  
 如果您的程式碼會在多個陳述式中存取相同物件，使用 `With` 陳述式有下列好處：  
  
- 您不需要多次評估複雜的運算式或指派結果給暫存變數，以多次參考其成員。  
  
- 您可以讓程式碼更容易讀取，方法是排除重複的限定運算式。  
  
 `objectExpression` 的資料類型可以是任何類別或結構類型，甚至是如 `Integer` 這類的 Visual Basic 基礎類型。  如果 `objectExpression` 會產生除了物件以外的任何項目，您可以只讀取其成員的值或叫用方法，如果嘗試指派值給 `With...End With` 陳述式中使用的結構成員，將會收到錯誤。  如果您叫用傳回結構的方法，並且立即存取和指派值給函式結果的成員 (例如 `GetAPoint().x = 1`)，便會收到這種相同錯誤。  這兩種情況下的問題是結構只存在於呼叫堆疊中，且在這些情況下沒有方法可以將修改過的結構成員寫入程式中其他程式碼可以觀察到變更的位置。  
  
 在進入區塊時，會評估 `objectExpression` 一次。 您無法從 `objectExpression` 區塊重新指派 `With`。  
  
 在 `With` 區塊中，您只能存取指定物件的方法和屬性，完全不需限定。 您可以使用其他物件的方法和屬性，但必須以其物件名稱加以限定。  
  
 您可以在另一個區塊中放置一個 `With...End With` 陳述式。 如果無法從內容清楚了解參考的物件，巢狀的 `With...End With` 陳述式可能會造成混淆。 當物件是從內部 `With` 區塊內參考時，您必須為外部 `With` 區塊中的物件提供完整參考。  
  
 您無法從區塊外部分支進入 `With` 陳述式區塊。  
  
 除非區塊包含迴圈，否則陳述式只會執行一次。 您可以巢狀方式處理不同種類的控制結構。 如需詳細資訊, 請參閱[嵌套控制項結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
> [!NOTE]
> 您可以在物件初始設定式中使用 `With` 關鍵字。 如需詳細資訊和範例, [請參閱物件初始化運算式:命名和匿名](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)型別和[匿名](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)型別。  
>   
>  如果您只有在初始化剛具現化之物件的屬性或欄位時使用 `With` 區塊，請考慮改用物件初始設定式。  
  
## <a name="example"></a>範例  
 在下列範例中，每個 `With` 區塊會在單一物件上執行一系列的陳述式。  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a>範例  
 下列範例會以巢狀方式處理 `With…End With` 陳述式。 在巢狀的 `With` 陳述式中，其語法會參考內部物件。  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.List%601>
- [巢狀控制結構](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [物件初始化運算式:命名和匿名型別](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名類型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)

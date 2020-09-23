---
title: 寬鬆委派轉換
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: b914d0479f160199744a8f9923c0bebc87321329
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086071"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>寬鬆委派轉換 (Visual Basic)

寬鬆委派轉換可讓您將子函數和函式指派給委派或處理常式，即使它們的簽章不相同也是一樣。 因此，系結至委派會與已允許進行方法調用的系結一致。  
  
## <a name="parameters-and-return-type"></a>參數和傳回類型  

 為了取代確切的簽章比對，當設定為時，寬鬆的轉換需要符合下列條件 `Option Strict` `On` ：  
  
- 擴輾轉換必須存在於每個委派參數的資料類型，以及所指派函式之對應參數的資料類型 `Sub` 。 在下列範例中，委派 `Del1` 有一個參數，也就是 `Integer` 。 `m`指派的 lambda 運算式中的參數，必須具有可進行擴輾轉換的資料類型 `Integer` ，例如 `Long` 或 `Double` 。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     只有當設定為時，才允許縮小轉換 `Option Strict` `Off` 。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- 從指派函式的傳回型別或委派的傳回型別，擴輾轉換必須存在於相反的方向 `Sub` 。 在下列範例中，每個指派的 lambda 運算式的主體都必須評估為擴展至的資料類型，因為的傳回 `Integer` 型別 `del1` 是 `Integer` 。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 如果 `Option Strict` 設定為 `Off` ，則會移除雙向的擴展限制。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>省略參數規格  

 寬鬆委派也可讓您完全省略指派方法中的參數規格：  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 請注意，您不能指定某些參數，並省略其他參數。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 省略參數的功能在某些情況下很有用，例如定義事件處理常式，其中牽涉到多個複雜參數。 不會使用某些事件處理常式的引數。 相反地，處理常式會直接存取註冊事件的控制項狀態，並忽略引數。 寬鬆委派可讓您在沒有任何多義性結果時省略這類宣告中的引數。 在下列範例中，可以將完整指定的方法 `OnClick` 改寫為 `RelaxedOnClick` 。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 範例  

 Lambda 運算式是在先前的範例中使用，可讓您輕鬆地查看型別關聯性。 不過，使用、或的委派指派也允許相同的 `AddressOf` 放寬 `Handles` `AddHandler` 。  
  
 在下列範例中，函式 `f1` 、 `f2` 、和都 `f3` `f4` 可以指派給 `Del1` 。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 下列範例只有在設為時才有效 `Option Strict` `Off` 。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>卸載函數傳回  

 寬鬆委派轉換可讓您將函式指派給 `Sub` 委派，以有效地忽略函數的傳回值。 不過，您無法將指派給函式 `Sub` 委派。 在下列範例中，會將函式的位址 `doubler` 指派給 `Sub` 委派 `Del3` 。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>另請參閱

- [Lambda 運算式](../procedures/lambda-expressions.md)
- [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)
- [委派](index.md)
- [如何：在 Visual Basic 中將程序傳遞至其他程序](how-to-pass-procedures-to-another-procedure.md)
- [區域型別推斷](../variables/local-type-inference.md)
- [Long](../../../language-reference/statements/option-strict-statement.md)

---
title: 區域類型推斷 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 59559f8775a5fd66a567897b009272df1727b1e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953335"
---
# <a name="local-type-inference-visual-basic"></a>區域類型推斷 (Visual Basic)
Visual Basic 編譯器會使用*型別推斷*來判斷未使用`As`子句宣告的本機變數資料類型。 編譯器會從初始化運算式的類型推斷變數的類型。 這可讓您宣告變數, 而不需要明確陳述型別, 如下列範例所示。 由於宣告的結果, `num1`和`num2`都是強型別做為整數。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
> 如果您不`num2`想在上一個範例中將輸入`Integer`為, 您可以使用或`Dim num4 As Double = 3`之類`Dim num3 As Object = 3`的宣告來指定另一個型別。  

> [!NOTE]
> 型別推斷只能用於非靜態的區域變數;它不能用來判斷類別欄位、屬性或函數的類型。
 
 區欄位型別推斷適用于程式層級。 它不能用來宣告模組層級的變數 (在類別、結構、模組或介面中, 而不是在程式或區塊內)。 如果`num2`上一個範例中的是類別的欄位, 而不是程式中的區域變數, 則宣告會造成`Option Strict`上的錯誤, `Object`而會將分類`num2`為的`Option Strict` 。 同樣地, 區欄位型別推斷不適用於宣告為`Static`的程式層級變數。  
  
## <a name="type-inference-vs-late-binding"></a>型別推斷與晚期繫結  
 使用型別推斷的程式碼類似依賴晚期繫結的程式碼。 不過, 類型推斷會強型別變數, 而不是將`Object`它保留為。 編譯器會在編譯時期使用變數的初始化運算式來判斷變數的類型, 以產生早期繫結程式碼。 在上述範例`num2` `num1`中, (例如) 的類型`Integer`為。  
  
 早期繫結變數的行為與晚期繫結變數的行為不同, 只有在執行時間才會知道該類型。 早期瞭解型別可讓編譯器在執行之前找出問題、精確配置記憶體, 以及執行其他優化。 早期繫結也會啟用 Visual Basic 的整合式開發環境 (IDE), 以提供有關物件成員的 IntelliSense 協助。 早期繫結也是效能的慣用選項。 這是因為晚期繫結變數中儲存的所有資料都必須包裝成型`Object`別, 而且在執行時間存取型別的成員會使程式變慢。  
  
## <a name="examples"></a>範例  
 宣告不含`As`子句的區域變數並初始化時, 就會發生型別推斷。 編譯器會使用指派之初始值的類型做為變數的類型。 例如, 下列每一行程式碼都會宣告一個型`String`別為的變數。  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 下列程式碼示範兩個對等的方式, 以建立整數陣列。  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 使用型別推斷來判斷迴圈控制變數的型別是很方便的。 在下列程式`Integer`代碼中, 編譯器會推斷`number`為, 因為`someNumbers2`先前範例中的是整數陣列。  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 區欄位型別推斷可以在語句中`Using`用來建立資源名稱的類型, 如下列範例所示。  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 您也可以從函式的傳回值推斷變數的類型, 如下列範例所示。 和都是進程陣列, 因為`Process.GetProcesses`會傳回進程陣列。 `pList2` `pList1`  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>選項推斷  
 `Option Infer`可讓您指定是否允許在特定檔案中使用區欄位型別推斷。 若要啟用或封鎖選項, 請在檔開頭輸入下列其中一個語句。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 如果您未`Option Infer`在程式碼中指定的值, 則編譯器預設值為`Option Infer On`。 
  
 如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。  
  
 如需詳細資訊, 請參閱[選項推斷語句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[編譯頁面、專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>另請參閱

- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

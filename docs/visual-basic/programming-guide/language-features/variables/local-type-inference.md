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
ms.openlocfilehash: b33b8b2d17c240e380377528d4f5d2f511381a7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="local-type-inference-visual-basic"></a>區域類型推斷 (Visual Basic)
Visual Basic 編譯器使用*型別推斷*來判斷資料類型的本機變數宣告為不具有`As`子句。 編譯器會推斷變數的初始化運算式的型別類型。 這可讓您宣告變數而不用明確陳述的型別，如下列範例所示。 宣告，因為兩者`num1`和`num2`強型別為整數。  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  如果您不想`num2`型別為前一個範例中`Integer`，您可以使用如下的宣告，以指定另一個類型`Dim num3 As Object = 3`或`Dim num4 As Double = 3`。  

> [!NOTE]
>  型別推斷只能用於非靜態區域變數。它不能用來判斷類別欄位、 屬性或函式的型別。
 
 區域類型推斷會套用在程序層級。 它不能用來宣告變數，在模組層級 （類別、 結構、 模組或介面內，但不是在程序或區塊）。 如果`num2`前一個範例中的欄位而非區域變數的程序中的類別，宣告會導致發生錯誤`Option Strict`，並會分類`num2`為`Object`與`Option Strict`關閉。 同樣地，區域類型推斷不適用於程序層級變數宣告為`Static`。  
  
## <a name="type-inference-vs-late-binding"></a>類型推斷 vs。晚期繫結  
 程式碼會使用類型推斷會類似程式碼所使用的晚期繫結。 不過，型別推斷強型別，而不要保持為變數`Object`。 編譯器會使用變數的初始設定式，來決定變數的類型在編譯時期產生早期繫結的程式碼。 在上述範例中， `num2`、 like `num1`，型別為`Integer`。  
  
 早期繫結變數的行為不同的晚期繫結變數，其只能在執行階段已知類型。 早期知道的型別，可讓編譯器在執行之前識別問題，明確地說，配置記憶體，並執行其他最佳化作業。 早期繫結也可讓 Visual Basic 的整合式的開發環境 (IDE) 提供 IntelliSense 會協助的相關物件的成員。 早期繫結也是慣用的效能。 這是因為晚期繫結變數中儲存的所有資料必須為類型都包裝`Object`，並在執行階段存取之類型成員的程式速度較慢。  
  
## <a name="examples"></a>範例  
 宣告本機變數不含任何時發生類型推斷`As`子句和初始化。 編譯器會使用指派的起始值的型別做為變數的類型。 例如，下列程式碼的每個宣告類型的變數`String`。  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 下列程式碼示範兩個對等的方式建立整數的陣列。  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 很容易就能使用類型推斷來判斷迴圈控制變數的類型。 下列程式碼，編譯器會推斷的`number`是`Integer`因為`someNumbers2`前一個範例是整數的陣列。  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 區域類型推斷可用於`Using`陳述式來建立資源名稱的型別，如下列範例所示。  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 變數的型別也推斷從函式的傳回值，如下列範例所示。 同時`pList1`和`pList2`是處理程序的陣列，因為`Process.GetProcesses`傳回處理程序的陣列。  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` 可讓您指定特定的檔案中是否允許區域類型推斷。 若要啟用或區塊的選項，請輸入下列陳述式的其中一個檔案的開頭。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 如果您未指定的值`Option Infer`編譯器預設值是您的程式碼`Option Infer On`。 針對從已升級的專案[!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)]或更早版本，編譯器預設值是`Option Infer Off`。  
  
 如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。  
  
 如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>另請參閱  
 [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next 陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

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
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052582"
---
# <a name="local-type-inference-visual-basic"></a>區域類型推斷 (Visual Basic)
Visual Basic 編譯器會使用*型別推斷*來判斷資料類型的未宣告的區域變數`As`子句。 編譯器會推斷變數的初始化運算式的類型的類型。 這可讓您宣告變數而不用明確陳述的型別，如下列範例所示。 宣告，因為兩者`num1`和`num2`強型別為整數。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  如果您不想`num2`在上述範例中做為型別`Integer`，您可以使用如下的宣告，以便指定另一個型別`Dim num3 As Object = 3`或`Dim num4 As Double = 3`。  

> [!NOTE]
>  型別推斷僅用於非靜態區域變數;它不能用來判斷類別欄位、 屬性或函式的型別。
 
 區域類型推斷會套用在程序層級。 它不能用來宣告變數，在模組層級 （在類別、 結構、 模組或介面，但不是在程序或區塊）。 如果`num2`在上述範例中的類別，而不是程序中的本機變數的欄位，宣告會導致發生錯誤`Option Strict`，並會分類`num2`作為`Object`與`Option Strict`關閉。 同樣地，區域類型推斷並不適用於程序層級變數宣告為`Static`。  
  
## <a name="type-inference-vs-late-binding"></a>類型推斷 vs。晚期繫結  
 使用型別推斷的程式碼類似於依賴晚期繫結的程式碼。 不過，類型推斷強型別，而非保留做為變數`Object`。 編譯器會使用變數的初始設定式，以判斷在編譯時期產生早期繫結的程式碼的變數的類型。 在上述範例中， `num2`，例如`num1`，輸入為`Integer`。  
  
 早期繫結變數的行為不同於晚期繫結變數，這只能在執行階段已知的型別。 早知道的型別，可讓編譯器執行之前識別問題、 精確地說，配置記憶體，並執行其他最佳化。 早期繫結也可讓 Visual Basic 的整合式的開發環境 (IDE) 的相關物件的成員提供 IntelliSense 協助。 早期繫結也十分適用於效能。 這是因為晚期繫結變數中儲存的所有資料必須為型別都包裝`Object`，並在執行階段存取類型的成員，會讓程式變慢。  
  
## <a name="examples"></a>範例  
 而不宣告的區域變數時發生類型推斷`As`子句和初始化。 編譯器會使用指派的起始值的型別，做為變數的類型。 例如，下列程式碼行的每個宣告類型的變數`String`。  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 下列程式碼示範兩個對等的方式，來建立整數的陣列。  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 它是方便使用類型推斷來判斷迴圈控制變數的型別。 下列程式碼中，編譯器會推斷所`number`是`Integer`因為`someNumbers2`前一個範例是一個整數的陣列。  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 區域類型推斷可用於`Using`陳述式來建立的資源名稱，型別，如下列範例所示。  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 變數的型別也從函式的傳回值推斷，如下列範例所示。 兩者`pList1`並`pList2`是處理程序的陣列，因為`Process.GetProcesses`傳回處理程序的陣列。  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` 可讓您指定特定的檔案中是否允許區域類型推斷。 若要啟用或封鎖選項，請輸入下列陳述式的其中一個，在檔案開頭。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 如果您未指定的值`Option Infer`在您的程式碼中，編譯器預設值是`Option Infer On`。 針對從升級的專案[!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)]或更早版本，編譯器預設值是`Option Infer Off`。  
  
 如果在檔案中設定給 `Option Infer` 的值與 IDE 或命令列中設定的值衝突，檔案中的值具有優先權。  
  
 如需詳細資訊，請參閱 < [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)並[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>另請參閱

- [匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

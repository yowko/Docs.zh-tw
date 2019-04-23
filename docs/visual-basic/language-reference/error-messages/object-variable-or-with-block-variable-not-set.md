---
title: 未設定物件變數或 With 區塊變數
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2c0c47b359e218111c1629ea574303a6d663046
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297924"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>未設定物件變數或 With 區塊變數
正在參考無效的物件變數。   發生這個錯誤的原因有下列幾種︰  
  
-   未指定類型所宣告的變數。 如果未指定的型別宣告變數，則預設為輸入`Object`。  
  
     例如，以宣告的變數`Dim x`的型別`Object;`以宣告的變數`Dim x As String`的型別`String`。  
  
    > [!TIP]
    >  `Option Strict`陳述式不允許隱含型別，會導致`Object`型別。 如果您省略類型時，會發生編譯時期錯誤。 請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
-   您嘗試參考已設定為物件 `Nothing`  
  
     。  
  
-   您嘗試存取未正確地宣告陣列變數的項目。  
  
     例如，陣列宣告為`products() As String`如果您嘗試參考陣列項目，將會觸發錯誤`products(3) = "Widget"`。 陣列沒有任何項目，並會被視為物件。  
  
-   您嘗試存取程式碼內`With...End With`區塊之前尚未初始化的區塊。   A`With...End With`區塊必須初始化執行`With`陳述式的進入點。  
  
> [!NOTE]
>  在舊版的 Visual Basic 或 VBA 這項錯誤也觸發指派給變數的值，而不使用`Set`關鍵字 (`x = "name"`而不是`Set x = "name"`)。 `Set`關鍵字已不再有效 Visual Basic.Net 中。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 設定`Option Strict`至`On`藉由將下列程式碼新增至檔案的開頭：  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2. 如果您不想要啟用`Option Strict`，搜尋您的程式碼所指定型別沒有任何變數 (`Dim x`而不是`Dim x As String`) 並將預定的型別新增至宣告。  
  
3. 請確定您已設定為物件變數不參考`Nothing`。  搜尋您的程式碼，關鍵字`Nothing`，和修訂您的程式碼，讓物件未設定為`Nothing`直到之後，您已參考它。  
  
4. 請確定陣列的任何變數建立維度，才能存取它們。 當您第一次建立陣列時，您可以是指派維度 (`Dim x(5) As String`而非`Dim x() As String`)，或使用`ReDim`設定陣列的維度，然後第一次存取關鍵字。  
  
5. 請確定您`With`區塊會藉由執行初始化`With`陳述式的進入點。  
  
## <a name="see-also"></a>另請參閱

- [物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

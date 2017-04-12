---
title: "物件變數或 With 區塊變數未設定 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
dev_langs:
- VB
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 820ef0115a6a27d77f10f4e41d95576bbd79bfa3
ms.lasthandoff: 03/13/2017

---
# <a name="object-variable-or-with-block-variable-not-set"></a>未設定物件變數或 With 區塊變數
正在參考無效的物件變數。   發生這個錯誤的原因有下列幾種︰  
  
-   變數已宣告但未指定的型別。 如果沒有指定型別宣告變數，則預設為輸入`Object`。  
  
     宣告的變數，例如`Dim x`屬於型別`Object;`所宣告的變數`Dim x As String`的型別會是`String`。  
  
    > [!TIP]
    >  `Option Strict`陳述式不允許隱含型別，而產生的`Object`型別。 如果您省略類型，就會發生編譯時期錯誤。 請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
-   您嘗試參考已設定為物件`Nothing`  
  
     。  
  
-   您嘗試存取的項目未正確宣告陣列變數。  
  
     例如，陣列宣告為`products() As String`如果您嘗試將參考陣列的項目將會觸發錯誤`products(3) = "Widget"`。 陣列沒有項目，因此會被視為物件。  
  
-   您嘗試存取程式碼內`With...End With`封鎖之前已初始化的區塊。   A`With...End With`區塊必須初始化執行`With`陳述式的進入點。  
  
> [!NOTE]
>  在舊版的 Visual Basic 或 VBA 此錯誤也已觸發的值指派給變數，而不需使用`Set`關鍵字 (`x = "name"`而不是`Set x = "name"`)。 `Set`關鍵字已不再有效，在 Visual Basic.Net。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  設定`Option Strict`至`On`檔案的開頭加入下列程式碼︰  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  如果您不想要啟用`Option Strict`，搜尋您指定了不具型別的任何變數的程式碼 (`Dim x`而不是`Dim x As String`)，並新增至宣告預期的類型。  
  
3.  請確定已設定為物件變數，您不參考`Nothing`。  搜尋關鍵字的程式碼`Nothing`，並修改您的程式碼，讓物件未設定為 `Nothing`直到您之後參考它。  
  
4.  請確定陣列的任何變數建立維度，才能存取它們。 您可以指派維度當您首次建立陣列 (`Dim x(5) As String`而不是`Dim x() As String`)，或使用`ReDim`關鍵字來設定陣列的維度，第一次存取之前。  
  
5.  請確定您`With`區塊會藉由執行初始化`With`陳述式的進入點。  
  
## <a name="see-also"></a>另請參閱  
 [物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)

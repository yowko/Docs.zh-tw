---
title: HOW TO：建立不會變更變數值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 57792db826caa996e163bc0a51b01a6bbd6a4858
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823320"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>HOW TO：建立不會變更變數值 (Visual Basic)
可能會互相矛盾，所以不會變更其值的變數概念。 但是常數不可行時，有很多情況下，而且最好有固定值的變數。 在這種情況中，您可以定義的成員變數[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。  
  
 您無法使用[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)來宣告和指派常數值在下列情況：  
  
-   `Const`陳述式不接受您想要使用的資料類型  
  
-   您在編譯時期不知道值  
  
-   無法在編譯時期計算的常數值  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>若要建立的變數，不會變更值  
  
1.  在模組層級宣告的成員變數[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)，並包含[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     您可以指定`ReadOnly`只能在成員變數上。 這表示您必須定義在模組層級，任何程序之外的變數。  
  
2.  您可以計算在編譯時期的單一陳述式中的值，如果使用中的初始化子句`Dim`陳述式。 請遵循[作為](../../../../visual-basic/language-reference/statements/as-clause.md)子句以等號 (`=`)，後面接著一個運算式。 請確定編譯器可以評估此運算式為常數的值。  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     您可以指派值給`ReadOnly`變數一次。 一旦您這樣做時，任何程式碼，可以不變更其值。  
  
     如果您在編譯時期不知道值，或無法計算它在編譯時期，在單一陳述式中，您仍然可以指派其建構函式在執行階段。 若要這樣做，您必須宣告`ReadOnly`類別或結構的層級變數。 在該類別或結構的建構函式，計算變數的固定的值，並從建構函式傳回之前將它指派給變數。  
  
## <a name="see-also"></a>另請參閱

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)

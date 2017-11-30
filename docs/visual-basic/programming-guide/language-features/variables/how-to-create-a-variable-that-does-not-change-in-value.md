---
title: "如何：建立不變更值的變數 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>如何：建立不變更值的變數 (Visual Basic)
可能會互相矛盾的概念，不會變更其值的變數。 但常數不可行時，有很多情況下，而且會很有用的變數，以固定值。 在這種情況下，您可以定義的成員變數[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。  
  
 您無法使用[Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)宣告並指派常數值，在下列情況下：  
  
-   `Const`陳述式不接受您想要使用的資料類型  
  
-   您不知道在編譯時期值  
  
-   無法在編譯時期計算常數值  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>若要建立不會變更變數值  
  
1.  在模組層級宣告的成員變數[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)，並包含[ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)關鍵字。  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     您可以指定`ReadOnly`只能在成員變數上。 這表示您必須定義在模組層級以外的任何程序的變數。  
  
2.  您可以計算在編譯時期單一陳述式中的值，如果使用中的初始化子句`Dim`陳述式。 請遵循[為](../../../../visual-basic/language-reference/statements/as-clause.md)子句以等號 (`=`)，後面接著一個運算式。 請務必編譯器可以評估此運算式為常數值。  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     您可以指派值給`ReadOnly`變數只能出現一次。 一旦您這樣做，程式碼不可以變更其值。  
  
     如果您不知道此值在編譯時期，或無法計算在編譯時期，單一陳述式中，您可以將它仍指派建構函式在執行階段。 若要這樣做，您必須宣告`ReadOnly`類別或結構的層級變數。 建構函式中該類別或結構，計算固定的值的變數，並從建構函式傳回之前將它指派給變數。  
  
## <a name="see-also"></a>另請參閱  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Const 陳述式](../../../../visual-basic/language-reference/statements/const-statement.md)

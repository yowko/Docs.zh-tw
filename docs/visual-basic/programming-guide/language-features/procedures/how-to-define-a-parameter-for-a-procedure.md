---
title: 如何：定義程序的參數 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb4bac9208c03fd18e1904f58b247824d2c215da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>如何：定義程序的參數 (Visual Basic)
A*參數*允許將值傳遞至程序呼叫它時，如果呼叫的程式碼。 您宣告一個變數，指定其名稱和資料類型的相同方式宣告的程序的每個參數。 您也可以指定傳遞機制，以及參數是否為選擇性。  
  
 如需詳細資訊，請參閱[程序參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-define-a-procedure-parameter"></a>若要定義程序參數  
  
1.  在程序宣告中，新增至程序的參數清單中，將其與其他參數逗點分隔的參數名稱。  
  
2.  決定參數的資料類型。  
  
3.  參數名稱之後加`As`子句來指定資料類型。  
  
4.  決定您想要用於參數的傳遞機制。 通常參數傳值方式傳遞，除非您想要能夠變更它的值，呼叫程式碼中的程序。  
  
5.  參數名稱前加[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)指定的傳遞機制。 如需詳細資訊，請參閱[差異之間傳遞引數的值和依參考](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
6.  如果參數是選擇性的在之前的傳遞機制，與[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)並遵循參數資料類型，以等號 (`=`) 和預設值。  
  
     下列範例會定義外框的`Sub`具有三個參數的程序。 前兩個所需和第三個是選擇性的。 參數宣告會以逗號分隔的參數清單中。  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     第一個參數接受`customer`物件，和`updateCustomer`可以直接更新變數傳遞給`c`因為引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。 此程序無法變更最後兩個引數的值，因為它們會傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。  
  
     如果呼叫程式碼並不提供的值`level`參數時，Visual Basic 將其設為預設值為 0。  
  
     如果類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off`、`As`子句是選擇性的當您定義的參數。 不過，如果任何一個參數使用`As`子句，全部都必須使用它。 類型檢查參數是否`On`、`As`子句是必要的每個參數定義。  
  
     指定資料類型的所有程式設計項目稱為*強型別*。 當您將`Option Strict On`，Visual Basic 會強制執行強式類型。 這強烈建議使用，原因如下：  
  
    -   它可讓您的變數和參數的 IntelliSense 支援。 這可讓您查看其屬性和其他成員，當您輸入程式碼中。  
  
    -   它可讓編譯器執行類型檢查。 這有助於 catch 陳述式可在執行階段因為例如溢位錯誤而失敗。 它也會對方法的呼叫攔截不支援它們的物件。  
  
    -   這樣可以更快地執行您的程式碼。 其中一個原因是，如果您未指定資料類型的程式設計項目，Visual Basic 編譯器將其指派`Object`型別。 可能需要編譯的程式碼之間來回轉換`Object`和其他資料類型，這會降低效能。  
  
## <a name="see-also"></a>另請參閱

 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [函式程序](./function-procedures.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [遞迴程序](./recursive-procedures.md)  
 [程序多載化](./procedure-overloading.md)  
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)  

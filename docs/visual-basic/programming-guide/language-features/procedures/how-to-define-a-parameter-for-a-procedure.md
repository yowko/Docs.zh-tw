---
title: "如何︰ 將參數定義程序 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedure parameters, defining data types for
- procedures, parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters, defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9fb9ad244499039c1768ff97f071168e0a0842e4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>如何：定義程序的參數 (Visual Basic)
A*參數*可讓呼叫的程式碼呼叫它時，將值傳遞至程序。 宣告每個參數的程序相同的方式宣告變數，指定其名稱和資料型別。 您也可以指定傳遞機制，以及是否為選擇性參數。  
  
 如需詳細資訊，請參閱[程序參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-define-a-procedure-parameter"></a>若要定義程序參數  
  
1.  在程序宣告中，新增至程序的參數清單，與其他參數分隔逗號分隔的參數名稱。  
  
2.  決定參數的資料型別。  
  
3.  參數名稱後面加上`As`子句來指定資料型別。  
  
4.  決定您想要將參數傳遞機制。 通常您傳遞參數值，除非您想要能夠變更其值在呼叫程式碼中的程序。  
  
5.  參數名稱前加[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)指定的傳遞機制。 如需詳細資訊，請參閱[差異之間傳遞引數的值和傳址](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
6.  如果參數是選擇性的在之前的傳遞機制，與[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)，並遵循參數資料類型，以等號 (`=`) 和預設值。  
  
     下列範例會定義的外框`Sub`使用三個參數的程序。 前兩個所需，且第三個為選用。 參數宣告會以逗號分隔的參數清單中。  
  
     [!code-vb[VbVbcnProcedures #&33;](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     第一個參數接受`customer`物件，和`updateCustomer`可以直接更新變數傳遞至`c`因為引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。 此程序無法變更的最後兩個引數的值，因為它們會傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。  
  
     如果呼叫程式碼沒有提供的值`level`參數，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將它設定為預設值為 0。  
  
     如果型別檢查切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off`、`As`子句是選擇性的當您定義的參數。 不過，如果任何一個參數使用`As`子句，全部都必須使用它。 如果檢查參數的型別`On`、`As`子句是針對每個參數定義必要的。  
  
     指定資料類型的所有程式設計項目稱為*強型別*。 當您設定`Option Strict On`，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會強制執行強型別。 強烈建議使用這個，原因如下︰  
  
    -   它可讓您的變數和參數的 IntelliSense 支援。 這可讓您查看其所有屬性和其他成員，當您輸入程式碼中。  
  
    -   它可讓編譯器執行類型檢查。 這有助於找出可能會在執行階段，因為例如溢位錯誤而失敗的陳述式。 也會對方法的呼叫攔截並不支援的物件。  
  
    -   這樣可以更快地執行您的程式碼。 原因是，如果您未指定資料類型的程式設計項目，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器將其指派`Object`型別。 可能需要編譯的程式碼之間來回轉換`Object`和其他資料類型，這會降低效能。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [Sub 程序](./sub-procedures.md)   
 [Function 程序](./function-procedures.md)   
 [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)   
 [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md)   
 [遞迴程序](./recursive-procedures.md)   
 [多載化程序](./procedure-overloading.md)   
 [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [物件導向程式設計](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)

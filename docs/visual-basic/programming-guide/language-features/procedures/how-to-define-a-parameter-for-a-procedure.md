---
title: HOW TO：將參數定義程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: 55925b0f007b1be2f5d46ffc0854601f483b2e2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863697"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>HOW TO：將參數定義程序 (Visual Basic)
A*參數*可讓呼叫端的程式碼呼叫它時，將值傳遞至程序。 宣告程序的每個參數相同的方式，您宣告一個變數，指定其名稱和資料型別。 您也可以指定傳遞機制，以及參數是否為選擇性。  
  
 如需詳細資訊，請參閱 <<c0> [ 程序參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-define-a-procedure-parameter"></a>若要定義程序參數  
  
1. 在程序宣告中，新增至程序的 [參數] 清單中，將其與其他參數逗點分隔的參數名稱。  
  
2. 決定參數的資料型別。  
  
3. 參數名稱後面加`As`子句來指定資料型別。  
  
4. 決定您所需參數的傳遞機制。 通常您為參數傳值方式傳遞，除非您想要能夠變更它的值，在呼叫程式碼中的程序。  
  
5. 使用參數名稱前面加上[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)指定的傳遞機制。 如需詳細資訊，請參閱 <<c0> [ 差異之間傳遞的引數的值和傳址](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
6. 如果參數是選擇性的在之前的傳遞機制，與[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)並遵循參數資料類型，以等號 (`=`) 和預設值。  
  
     下列範例會定義外框的`Sub`使用三個參數的程序。 前兩個所需，且選擇性第三個。 參數宣告會以逗號分隔的參數清單中。  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     第一個參數會接受`customer`物件，並`updateCustomer`可以直接更新變數傳遞給`c`因為引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。 此程序無法變更的最後兩個引數的值，因為它們會傳遞[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。  
  
     如果呼叫程式碼未提供的值`level`參數，Visual Basic 將其設為預設值為 0。  
  
     如果類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off`，則`As`子句是選擇性的當您定義的參數。 不過，如果任何一個參數使用`As`子句，所有人都必須使用它。 類型檢查參數是否`On`，則`As`子句是必要的每個參數定義。  
  
     指定所有程式設計項目的資料型別就所謂*強型別*。 當您將設定`Option Strict On`，Visual Basic 會強制執行強型別。 這是強烈建議，原因如下：  
  
    -   它可讓您的變數和參數的 IntelliSense 支援。 這可讓您查看其屬性與其他成員，當您輸入程式碼中。  
  
    -   它可讓編譯器執行類型檢查。 這有助於攔截可能會在執行階段因例如溢位錯誤而失敗的陳述式。 它也會對方法的呼叫攔截不支援它們的物件。  
  
    -   它會導致您的程式碼的執行速度加快。 其原因之一是，如果您未指定資料類型的程式設計項目，則 Visual Basic 編譯器將其指派`Object`型別。 您已編譯的程式碼可能必須將之間來回轉換`Object`及其他資料類型，會降低效能。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [遞迴程序](./recursive-procedures.md)
- [程序多載化](./procedure-overloading.md)
- [物件和類別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)

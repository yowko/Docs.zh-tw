---
title: 如何：定義程序的參數
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: e703346113348556b8a3ea41a7934a55a8008522
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388072"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>如何：定義程序的參數 (Visual Basic)
*參數*可讓呼叫程式碼在呼叫它時，將值傳遞給程式。 您可以使用宣告變數的相同方式來宣告程式的每個參數，並指定其名稱和資料類型。 您也可以指定傳遞機制，以及參數是否為選擇性。  
  
 如需詳細資訊，請參閱程式[參數和引數](./procedure-parameters-and-arguments.md)。  
  
### <a name="to-define-a-procedure-parameter"></a>若要定義程式參數  
  
1. 在程式宣告中，將參數名稱新增至程式的參數清單，並以逗號分隔它與其他參數。  
  
2. 決定參數的資料類型。  
  
3. 請在參數名稱後面加上 `As` 子句，以指定資料類型。  
  
4. 決定您想要用於參數的傳遞機制。 一般來說，您會以傳值方式傳遞參數，除非您想要讓程式能夠在呼叫程式碼中變更其值。  
  
5. 在參數名稱前面加上[ByVal](../../../language-reference/modifiers/byval.md)或[ByRef](../../../language-reference/modifiers/byref.md) ，以指定傳遞機制。 如需詳細資訊，請參閱[依值和傳址方式傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)。  
  
6. 如果參數是選擇性的，請在傳遞機制之前加上[選擇性](../../../language-reference/modifiers/optional.md)，並遵循具有等號（ `=` ）和預設值的參數資料類型。  
  
     下列範例會定義 `Sub` 具有三個參數之程式的外框。 前兩個是必要的，而第三個是選擇性的。 參數宣告會在參數清單中以逗號分隔。  
  
     [!code-vb[VbVbcnProcedures#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#33)]  
  
     第一個參數會接受 `customer` 物件，而且 `updateCustomer` 可以直接更新傳遞給的變數， `c` 因為引數是以[ByRef](../../../language-reference/modifiers/byref.md)傳遞。 程式無法變更最後兩個引數的值，因為它們會傳遞[ByVal](../../../language-reference/modifiers/byval.md)。  
  
     如果呼叫程式碼未提供參數的值 `level` ，Visual Basic 會將它設定為預設值0。  
  
     如果類型檢查參數（[Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)）為 `Off` ，則 `As` 當您定義參數時，子句是選擇性的。 不過，如果有任何一個參數使用 `As` 子句，則其全部都必須使用它。 如果類型檢查參數為 `On` ，則 `As` 每個參數定義都需要子句。  
  
     指定所有程式設計項目的資料類型，就稱為*強*型別。 當您設定時 `Option Strict On` ，Visual Basic 會強制執行強式類型。 強烈建議您這麼做，原因如下：  
  
    - 它會針對您的變數和參數啟用 IntelliSense 支援。 這可讓您在程式碼中輸入時，看到其屬性和其他成員。  
  
    - 它可讓編譯器執行類型檢查。 這有助於攔截在執行時間因溢位之類的錯誤而失敗的語句。 它也會攔截不支援之物件上方法的呼叫。  
  
    - 這會導致程式碼的執行速度更快。 其中一個原因是，如果您沒有指定程式設計項目的資料類型，Visual Basic 編譯器會為它指派 `Object` 類型。 您已編譯的程式碼可能必須在 `Object` 和其他資料類型之間來回轉換，以降低效能。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [Function 程序](./function-procedures.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [遞迴程序](./recursive-procedures.md)
- [程序多載化](./procedure-overloading.md)
- [物件和類別](../objects-and-classes/index.md)
- [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)

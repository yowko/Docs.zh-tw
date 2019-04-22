---
title: 程序參數和引數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: 80065cabcacdcf44b04fef7bacb978ca9c8077ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825452"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>程序參數和引數 (Visual Basic)
在大部分情況下，程序會需要一些資訊在其中呼叫的情況。 執行重複或共用工作的程序會針對每個呼叫中使用不同的資訊。 這項資訊是由變數、 常數和您傳遞至程序時呼叫它的運算式所組成。  
  
 A*參數*表示程序需要您提供當您呼叫它的值。 程序的宣告會定義其參數。  
  
 您可以定義具有任何參數，一個參數，或一個以上的程序。 在呼叫程序定義指定之參數的一部分*參數清單*。  
  
 *引數*程序參數代表您提供的值，當您呼叫程序。 呼叫程序時，呼叫程式碼會提供引數。 指定的引數的程序呼叫的部分稱為*引數清單*。  
  
 下圖顯示程式碼呼叫程序`safeSquareRoot`從兩個不同的地方。 第一次呼叫會將變數的值傳遞`x`(4.0) 參數`number`，並在傳回的值`root`(2.0) 指派給變數`y`。 第二次呼叫會將傳遞常值數值 9.0 `number`，並將傳回的值 (3.0) 指派給變數`z`。  
  
 ![此圖顯示傳遞至參數的引數](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 如需詳細資訊，請參閱 <<c0> [ 參數之間的差異和引數](./differences-between-parameters-and-arguments.md)。  
  
## <a name="parameter-data-type"></a>參數資料類型  
 您定義資料類型的參數使用`As`在其宣告中的子句。 例如，下列函式會接受字串和整數。  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 如果類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`Off,``As`子句是選擇性的不同之處在於任何一個參數會使用它，如果所有參數必須都使用它。 如果型別檢查`On`，則`As`子句是必要的所有程序參數。  
  
 如果呼叫程式碼必須要有這類資料類型不同，其對應的參數提供引數`Byte`至`String`參數，它必須執行下列其中一項：  
  
-   提供引數會擴展為參數的資料型別; 的資料類型  
  
-   設定`Option Strict Off`允許隱含的縮小轉換; 或  
  
-   您可以使用轉換關鍵字，明確轉換成資料類型。  
  
### <a name="type-parameters"></a>類型參數  
 A*泛型程序*也會定義一或多個*型別參數*除了其一般的參數。 泛型程序可讓呼叫端的程式碼，來傳遞不同的資料類型每次呼叫此程序，讓它可以調整資料類型需求的每個個別的呼叫。 請參閱 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [如何：如需程序來定義參數](./how-to-define-a-parameter-for-a-procedure.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [程序多載化](./procedure-overloading.md)
- [在 Visual Basic 中的類型轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)

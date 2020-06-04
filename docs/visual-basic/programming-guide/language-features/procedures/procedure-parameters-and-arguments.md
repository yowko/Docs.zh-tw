---
title: 程序參數和引數
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
ms.openlocfilehash: 178206ca2ee103bbdb5a4ac03bca0df903c8c5d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406712"
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a>程序參數和引數 (Visual Basic)
在大部分的情況下，程式需要一些有關已呼叫它的情況的資訊。 執行重複或共用工作的程式會針對每個呼叫使用不同的資訊。 這項資訊是由您在呼叫它時傳遞給程式的變數、常數和運算式所組成。  
  
 *參數*代表當您呼叫它時，程式預期會提供的值。 程式的宣告會定義其參數。  
  
 您可以定義不含任何參數、一個參數或一個以上的程式。 指定參數之程序定義的部分稱為「參數清單」（ *parameter list*）。  
  
 *引數*代表當您呼叫程式時，您提供給程式參數的值。 呼叫程式碼會在呼叫程式時提供引數。 程序呼叫中指定引數的部分稱為*引數清單*。  
  
 下圖顯示 `safeSquareRoot` 從兩個不同的位置呼叫程式的程式碼。 第一個呼叫會將變數的值 `x` （4.0）傳遞給參數 `number` ，並將（2.0）中的傳回值 `root` 指派給變數 `y` 。 第二個呼叫會將常值9.0 傳遞至 `number` ，並將傳回值（3.0）指派給變數 `z` 。  
  
 ![顯示將引數傳遞至參數的圖表](./media/procedure-parameters-and-arguments/pass-argument-parameter.gif)  
  
 如需詳細資訊，請參閱[參數和引數之間的差異](./differences-between-parameters-and-arguments.md)。  
  
## <a name="parameter-data-type"></a>參數資料類型  
 您可以在其宣告中使用子句，以定義參數的資料類型 `As` 。 例如，下列函數會接受字串和整數。  
  
 [!code-vb[VbVbcnProcedures#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#32)]  
  
 如果類型檢查參數（[Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)）是 `Off,` 選擇性的 `As` 子句，但如果有任何一個參數使用它，則所有參數都必須使用它。 如果類型檢查為 `On` ，則 `As` 所有程式參數都需要子句。  
  
 如果呼叫程式碼預期提供的引數與其對應參數的資料類型不同，例如 `Byte` `String` 參數，則必須執行下列其中一項動作：  
  
- 僅提供資料類型為的引數，可擴大為參數資料類型;  
  
- 設定 `Option Strict Off` 為允許隱含的縮小轉換; 或  
  
- 使用轉換關鍵字來明確轉換資料類型。  
  
### <a name="type-parameters"></a>類型參數  
 *泛型*程式也會定義一或多個*型別參數*，以及其一般參數。 泛型程式可讓呼叫程式碼在每次呼叫程式時傳遞不同的資料類型，因此它可以根據每個個別呼叫的需求來量身訂做資料類型。 請參閱 [Generic Procedures in Visual Basic](../data-types/generic-procedures.md)。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [Function 程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [如何：定義程序的參數](./how-to-define-a-parameter-for-a-procedure.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [程序多載化](./procedure-overloading.md)
- [Visual Basic 中的類型轉換](../data-types/type-conversions.md)

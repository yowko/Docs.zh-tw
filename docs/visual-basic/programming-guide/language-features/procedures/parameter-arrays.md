---
title: 參數陣列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 5a2813b81490e7c2fcf1abcf5fd36ca89d9d7929
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933851"
---
# <a name="parameter-arrays-visual-basic"></a>參數陣列 (Visual Basic)
通常, 您不能使用比程式宣告指定的多個引數來呼叫程式。 當您需要不限數目的引數時, 您可以宣告*參數陣列*, 讓程式接受參數值陣列。 當您定義程式時, 不需要知道參數陣列中的元素數目。 陣列大小是由程式的每個呼叫個別決定。  
  
## <a name="declaring-a-paramarray"></a>宣告 ParamArray  
 您可以使用[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)關鍵字來表示參數清單中的參數陣列。 可套用下列規則：  
  
- 程式只能定義一個參數陣列, 而且它必須是程序定義中的最後一個參數。  
  
- 參數陣列必須以傳值方式傳遞。 在程序定義中明確包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)關鍵字是良好的程式設計作法。  
  
- 參數陣列是自動選擇的。 其預設值為參數陣列的元素類型的一維空陣列。  
  
- 參數陣列前面的所有參數都必須是必要的。 參數陣列必須是唯一的選擇性參數。  
  
## <a name="calling-a-paramarray"></a>呼叫 ParamArray  
 當您呼叫定義參數陣列的程式時, 您可以使用下列任何一種方式提供引數:  
  
- 沒有, 也就是說, 您可以省略[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引數。 在此情況下, 會將空的陣列傳遞給程式。 您也可以傳遞「[無](../../../../visual-basic/language-reference/nothing.md)關鍵字」的相同效果。  
  
- 任意數目的引數清單 (以逗號分隔)。 每個引數的資料類型必須可以隱含地轉換`ParamArray`成元素類型。  
  
- 陣列, 其元素類型與參數陣列的元素類型相同。  
  
 在所有情況下, 程式內的程式碼會將參數陣列視為一維陣列, 其中包含與`ParamArray`資料類型相同之資料類型的元素。  
  
> [!IMPORTANT]
> 當您處理可能會無限大的陣列時, 會有 overrunning 應用程式的一些內部容量的風險。 如果您接受參數陣列, 您應該測試呼叫程式碼傳遞給它的陣列大小。 如果您的應用程式太大, 請採取適當的步驟。 如需詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會定義和呼叫`calcSum`函式。 `ParamArray` 參數`args`的修飾詞可讓函式接受可變數目的引數。  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 下列範例會定義具有參數陣列的程式, 並輸出傳遞至參數陣列之所有陣列元素的值。  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)
- [選擇性參數](./optional-parameters.md)
- [程序多載化](./procedure-overloading.md)
- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)

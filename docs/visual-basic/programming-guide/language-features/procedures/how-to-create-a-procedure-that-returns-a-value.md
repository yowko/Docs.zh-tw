---
title: 如何：建立傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 2655aba6ce37be831d8dd4202ffd484cfd3fd5ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388345"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>如何：建立傳回值的程序 (Visual Basic)
您可以使用程式 `Function` ，將值傳回給呼叫程式碼。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>若要建立會傳回值的程式  
  
1. 在任何其他程式之外，請使用 `Function` 語句，後面接著 `End Function` 語句。  
  
2. 在 `Function` 語句中，在 `Function` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單。  
  
3. 請在括弧後面加上 `As` 子句，以指定傳回值的資料類型。  
  
4. 將程式的程式碼語句放在 `Function` 和 `End Function` 語句之間。  
  
5. 使用 `Return` 語句，將值傳回給呼叫程式碼。  
  
     下列 `Function` 程式會計算直角三角形的最長邊（或斜邊），並指定其他兩邊的值。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     下列範例顯示的一般呼叫 `hypotenuse` 。  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Function 陳述式](../../../language-reference/statements/function-statement.md)
- [如何：傳回程序的值](./how-to-return-a-value-from-a-procedure.md)
- [如何：呼叫傳回值的程序](./how-to-call-a-procedure-that-returns-a-value.md)

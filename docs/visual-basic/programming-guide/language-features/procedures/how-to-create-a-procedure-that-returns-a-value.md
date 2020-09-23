---
title: 如何：建立傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 3d28162d2a2103477a20b08fc03c937de8b5a475
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071868"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>如何：建立傳回值的程序 (Visual Basic)

您可以使用程式 `Function` ，將值傳回給呼叫程式碼。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>若要建立傳回值的程式  
  
1. 在任何其他程式之外，請使用 `Function` 語句，然後使用語句 `End Function` 。  
  
2. 在語句中，以程式的 `Function` `Function` 名稱後面加上關鍵字，然後以括弧括住參數清單。  
  
3. 在括弧後面加上 `As` 子句，以指定傳回值的資料類型。  
  
4. 在和語句之間放置程式的程式碼語句 `Function` `End Function` 。  
  
5. 使用 `Return` 語句將值傳回給呼叫程式碼。  
  
     下列 `Function` 程式會計算出右邊三角形的最長邊（或斜邊），並指定其他兩側的值。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     下列範例顯示一般的呼叫 `hypotenuse` 。  
  
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

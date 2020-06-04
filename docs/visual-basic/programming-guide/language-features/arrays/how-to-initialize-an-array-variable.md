---
title: 如何：初始化陣列變數
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 7feaf71fa1c59c24aa751f2b9e28328d47ba357c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413062"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>如何：在 Visual Basic 中初始化陣列變數
您可以藉由在子句中包含陣列常 `New` 值並指定陣列的初始值，初始化陣列變數。 您可以指定類型，或允許它從陣列常值中的值推斷。 如需如何推斷類型的詳細資訊，請參閱[陣列](index.md)中的「以初始值填入陣列」。  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>若要使用陣列常值來初始化陣列變數  
  
- 不論是在 `New` 子句中，或是當您指派陣列值時，請在大括弧（）內提供元素值 `{}` 。 下列範例示範幾種宣告、建立和初始化變數的方式，以包含具有類型之元素的陣列 `Char` 。  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     在執行每個語句之後，所建立的陣列的長度為3，而索引0到索引2的元素包含初始值。 如果您同時提供上限和值，就必須在索引0到上限的每個元素中包含一個值。  
  
     請注意，如果您在陣列常值中提供元素值，則不需要指定索引上限。 如果未指定上限，陣列的大小會根據陣列常值中的值數目來推斷。  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>若要使用陣列常值來初始化多維度陣列變數  
  
- 在大括弧內的大括弧（）內嵌套值 `{}` 。 確定所有嵌套陣列常值都會推斷為相同類型和長度的陣列。 下列程式碼範例顯示多維度陣列初始化的幾個範例。  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- 您可以明確指定陣列界限，或將其保留出來，然後讓編譯器根據陣列常值中的值來推斷陣列界限。 如果您同時提供上限和值，則必須在每個維度的上限中包含索引0的每個元素的值。 下列範例示範幾種宣告、建立和初始化變數的方式，以包含具有類型之元素的二維陣列。`Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     在每個語句執行之後，所建立的陣列會包含六個已初始化的元素，這些專案具有索引 `(0,0)` 、 `(0,1)` 、 `(0,2)` 、 `(1,0)` 、 `(1,1)` 和 `(1,2)` 。 每個陣列位置都會包含值 `10` 。  
  
- 下列範例會逐一查看多維陣列。 在以 Visual Basic 撰寫的 Windows 主控台應用程式中，貼上方法內的程式碼 `Sub Main()` 。 最後一個批註會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>若要使用陣列常值來初始化不規則陣列變數  
  
- 在大括弧（）內嵌套物件值 `{}` 。 雖然您也可以將指定不同長度陣列的陣列常值（如果是不規則陣列）加以嵌套，請確定已將嵌套陣列常值括在括弧中（ `()` ）。 括弧會強制評估嵌套陣列常值，而產生的陣列會當做不規則陣列的初始值使用。 下列程式碼範例顯示不規則陣列初始化的兩個範例。  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- 下列範例會逐一查看不規則陣列。 在以 Visual Basic 撰寫的 Windows 主控台應用程式中，貼上方法內的程式碼 `Sub Main()` 。  程式碼中的最後一個批註會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>另請參閱

- [陣列](index.md)
- [針對陣列進行疑難排解](troubleshooting-arrays.md)

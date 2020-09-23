---
title: 如何：初始化陣列變數
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 1add054a6cb6468f4581f92ca3a258c5b0cdc77d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058855"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>如何：在 Visual Basic 中初始化陣列變數

您可以藉由在子句中包含陣列常 `New` 值並指定陣列的初始值，來初始化陣列變數。 您可以指定類型，或允許從陣列常值中的值推斷。 如需如何推斷類型的詳細資訊，請參閱 [陣列](index.md)中的「以初始值填入陣列」。  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>使用陣列常值初始化陣列變數  
  
- 在子句中 `New` ，或當您指派陣列值時，提供括弧內的元素值 (`{}`) 。 下列範例示範幾種宣告、建立及初始化變數的方式，以包含具有類型之元素的陣列 `Char` 。  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     在每個語句執行之後，所建立的陣列都有一個長度為3的元素，而索引0到索引2的專案包含初始值。 如果您同時提供上限和值，就必須將索引0中的每個元素的值包含在上限的上方。  
  
     請注意，如果您在陣列常值中提供元素值，就不需要指定索引上限。 如果未指定上限，則會根據陣列常值中的值數目推斷陣列的大小。  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>使用陣列常值初始化多維度陣列變數  
  
- 在大括弧內將值嵌套 (`{}`) 。 確定嵌套陣列常值全都推斷為相同類型和長度的陣列。 下列程式碼範例顯示多維度陣列初始化的數個範例。  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- 您可以明確指定陣列界限，或將其保留出來，並讓編譯器根據陣列常值中的值推斷陣列界限。 如果您同時提供上限和值，就必須在每個維度中，包含索引0到上限的每個專案的值。 下列範例示範幾種宣告、建立及初始化變數的方式，以包含具有類型之元素的二維陣列。 `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     在每個語句執行之後，所建立的陣列就會包含六個具有索引、、、、和的初始化元素 `(0,0)` `(0,1)` `(0,2)` `(1,0)` `(1,1)` `(1,2)` 。 每個陣列位置都包含值 `10` 。  
  
- 下列範例會逐一查看多維陣列。 在以 Visual Basic 撰寫的 Windows 主控台應用程式中，將程式碼貼到 `Sub Main()` 方法中。 最後一個批註會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>使用陣列常值初始化不規則陣列變數  
  
- 在大括弧內將物件值 (`{}`) 。 雖然您也可以將指定不同長度陣列的陣列常值進行嵌套，但在不規則陣列的情況下，請確定嵌套陣列常值以括弧括住 (`()`) 。 括弧會強制執行嵌套陣列常值的評估，而產生的陣列會用來做為不規則陣列的初始值。 下列程式碼範例顯示兩個不規則陣列初始化的範例。  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- 下列範例會逐一查看不規則的陣列。 在以 Visual Basic 撰寫的 Windows 主控台應用程式中，將程式碼貼到 `Sub Main()` 方法中。  程式碼中的最後一個批註會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>另請參閱

- [陣列](index.md)
- [針對陣列進行疑難排解](troubleshooting-arrays.md)

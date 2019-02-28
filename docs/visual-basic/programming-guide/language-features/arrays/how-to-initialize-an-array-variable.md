---
title: HOW TO：初始化陣列變數在 Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 069c03cc9666cffec2edd26afeb86f0230f9bc6f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980928"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>HOW TO：初始化陣列變數在 Visual Basic
包括陣列常值中初始化陣列變數`New`子句並指定陣列的初始值。 您可以指定的型別，或允許它從陣列常值中的值推斷。 如需如何推斷的類型的詳細資訊，請參閱 < 填入陣列與初始值 」 中[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>若要使用陣列常值初始化陣列變數  
  
-   處於`New`子句，或當您指派陣列值，提供在括號內的項目值 (`{}`)。 下列範例示範數種方式可宣告、 建立和初始化變數，以包含陣列元素型別為`Char`。  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     每個陳述式執行之後，建立陣列長度為 3，包含位於索引 0 到索引 2 包含的起始值的項目。 如果您提供上限和值，您必須包含每個項目，從索引 0 到上限的值。  
  
     請注意，您不需要指定索引上限，如果您提供陣列常值中的項目值。 如果指定沒有上限，則是會依據陣列常值中的值數目來推斷陣列的大小。  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>若要使用陣列常值初始化多維陣列變數  
  
-   巢狀括號內的值 (`{}`) 大括號內。 請確認巢狀的陣列常值全都會推斷為相同的類型和長度的陣列。 下列程式碼範例示範數個多維陣列初始化範例。  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
-   您可以明確指定陣列界限，或省略它們，然後讓編譯器推斷陣列界限依據陣列常值中的值。 如果您提供上限與值，您必須包含每個項目，從索引 0 到上限的值，每個維度。 下列範例示範數種方式可宣告、 建立和初始化變數，以包含元素為類型的二維陣列 `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     每個陳述式執行之後，建立的陣列會包含六個初始化的元素，其索引`(0,0)`， `(0,1)`， `(0,2)`， `(1,0)`， `(1,1)`，和`(1,2)`。 每個陣列位置都包含值`10`。  
  
-   下列範例中逐一查看多維陣列。 在以 Visual Basic 撰寫的 Windows 主控台應用程式，貼上內部的程式碼`Sub Main()`方法。 最後一個註解會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>若要使用陣列常值初始化不規則的陣列變數  
  
-   巢狀括號內的物件值 (`{}`)。 雖然您也可以巢狀陣列常值，指定陣列的長度不同，在不規則的陣列，請確定巢狀的陣列常值會括在括號中 (`()`)。 括號會強制評估巢狀的陣列常值和產生的陣列做為不規則陣列的初始值。 下列程式碼範例示範兩個不規則的陣列初始化範例。  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
-   下列範例中逐一查看不規則陣列。 在以 Visual Basic 撰寫的 Windows 主控台應用程式，貼上內部的程式碼`Sub Main()`方法。  在程式碼中的最後一個註解會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>另請參閱
- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)

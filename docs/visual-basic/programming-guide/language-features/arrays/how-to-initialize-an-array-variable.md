---
title: "如何：在 Visual Basic 中初始化陣列變數"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3ccdbed601d3fa87acb0833bc153c199b17a4eba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>如何：在 Visual Basic 中初始化陣列變數
包括陣列常值中初始化陣列變數`New`子句，並指定陣列的初始值。 您可以指定類型，或讓它從陣列常值中的值推斷。 如需如何推斷的類型的詳細資訊，請參閱"填入陣列與初始值"[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>使用陣列常值初始化陣列變數  
  
-   有兩種`New`子句，或當您指定的陣列值，提供在括號內的項目值 (`{}`)。 下列範例示範幾種方式可以宣告、 建立和初始化變數，以包含具有類型的項目陣列`Char`。  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     每個陳述式執行之後，建立的陣列長度為 3，位於索引 0 到索引 2 包含起始值的項目。 如果您提供的上限和值，您必須包含每個項目，從索引 0 到上限的值。  
  
     請注意，您不需要指定索引上限，如果您提供陣列常值中的項目值。 如果指定沒有上限，則是會依據陣列常值中的值數目來推斷陣列的大小。  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>使用陣列常值初始化多維陣列變數  
  
-   巢狀括號內的值 (`{}`) 大括號內。 請確定所有推斷陣列的相同類型和長度的巢狀的陣列常值。 下列程式碼範例顯示數個多維度陣列初始化範例。  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   明確指定陣列界限或省略它們即可讓編譯器推斷陣列常值中的值為基礎的陣列界限。 如果您提供的上限和值，您必須包含每個項目，從索引 0 到上限的值，每個維度。 下列範例示範幾種方式可以宣告、 建立和初始化變數，以包含具有類型的元素的二維陣列`Short`  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     每個陳述式執行之後，建立的陣列會包含六個初始化的項目有索引`(0,0)`， `(0,1)`， `(0,2)`， `(1,0)`， `(1,1)`，和`(1,2)`。 每個陣列的位置包含值`10`。  
  
-   下列範例逐一查看多維陣列。 在 Visual Basic 中寫入 Windows 主控台應用程式，在貼上內的程式碼`Sub Main()`方法。 最後一個註解會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>使用陣列常值初始化不規則的陣列變數  
  
-   巢狀括號內的物件值 (`{}`)。 雖然您也可以巢狀陣列常值，指定陣列長度不同，如果是不規則的陣列，請確定巢狀的陣列常值括在括號中 (`()`)。 括號會強制評估的巢狀的陣列常值和不規則陣列的起始值為使用產生的陣列。 下列程式碼範例示範不規則的陣列初始化兩個範例。  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   下列範例會逐一不規則陣列。 在 Visual Basic 中寫入 Windows 主控台應用程式，在貼上內的程式碼`Sub Main()`方法。  在程式碼中的最後一個註解會顯示輸出。  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [陣列的疑難排解](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)

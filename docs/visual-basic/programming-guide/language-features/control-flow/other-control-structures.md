---
title: 其他控制結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c42070ce2ea866e59e1b2e190f7c05e1ee7cc922
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819316"
---
# <a name="other-control-structures-visual-basic"></a>其他控制結構 (Visual Basic)
Visual Basic 提供可協助您控制結構處置資源，或減少您必須重複的物件參考的次數。  
  
## <a name="usingend-using-construction"></a>使用...使用建構的結束  
 `Using...End Using`建構建立陳述式區塊，請在其中使用的資源，例如 SQL 連接。 您可以選擇性地取得的資源`Using`陳述式。 當您結束`Using`區塊時，Visual Basic 自動處置該資源使其可供其他程式碼，以使用。 資源必須是本機和可處置。 如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>與...建構的結尾  
 `With...End With`建構可讓您一次指定的物件參考，然後再執行一系列存取其成員的陳述式。 這可以簡化程式碼，並改善效能，因為 Visual Basic 不需要重新建立每個陳述式來存取它的參考。 如需詳細資訊，請參閱[與...With...end With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。  
  
## <a name="see-also"></a>另請參閱

- [控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [巢狀控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)
- [With...End With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)

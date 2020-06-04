---
title: 其他控制結構
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402014"
---
# <a name="other-control-structures-visual-basic"></a>其他控制結構 (Visual Basic)
Visual Basic 提供控制結構，協助您處置資源，或減少必須重複物件參考的次數。  
  
## <a name="usingend-using-construction"></a>使用 .。。使用結構結束  
 此 `Using...End Using` 結構會建立一個語句區塊，您可以在其中使用 SQL 連接之類的資源。 您可以選擇性地使用語句取得資源 `Using` 。 當您結束 `Using` 區塊時，Visual Basic 會自動處置資源，使其可供其他程式碼使用。 資源必須是本機且可處置的。 如需詳細資訊，請參閱[Using 語句](../../../language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>使用 .。。以結構結束  
 此 `With...End With` 結構可讓您指定一次物件參考，然後執行一系列存取其成員的語句。 這可簡化您的程式碼並改善效能，因為 Visual Basic 不需要為存取它的每個語句重新建立參考。 如需詳細資訊，請參閱[With .。。結尾為語句](../../../language-reference/statements/with-end-with-statement.md)。  
  
## <a name="see-also"></a>另請參閱

- [控制流程](index.md)
- [決策結構](decision-structures.md)
- [迴圈結構](loop-structures.md)
- [巢狀控制結構](nested-control-structures.md)
- [Using 語句](../../../language-reference/statements/using-statement.md)
- [With...End With 陳述式](../../../language-reference/statements/with-end-with-statement.md)

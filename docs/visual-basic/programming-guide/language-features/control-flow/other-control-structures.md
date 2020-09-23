---
title: 其他控制結構
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 8e7ca699e532ac7cfbe7918d850e7a28d1b27bcf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058608"
---
# <a name="other-control-structures-visual-basic"></a>其他控制結構 (Visual Basic)

Visual Basic 提供控制結構，可協助您處置資源或減少您必須重複物件參考的次數。  
  
## <a name="usingend-using-construction"></a>使用。。。結束使用結構  

 此 `Using...End Using` 結構會建立語句區塊，而您可以在其中使用 SQL 連接之類的資源。 您可以選擇性地使用語句取得資源 `Using` 。 當您結束 `Using` 區塊時，Visual Basic 會自動處置資源，使其可供其他程式碼使用。 資源必須是本機且可處置的。 如需詳細資訊，請參閱 [Using 語句](../../../language-reference/statements/using-statement.md)。  
  
## <a name="withend-with-construction"></a>使用 .。。以結構結尾  

 此 `With...End With` 結構可讓您指定一次物件參考，然後執行一系列存取其成員的語句。 這可以簡化您的程式碼並改善效能，因為 Visual Basic 不需要為每個存取它的語句重新建立參考。 如需詳細資訊，請參閱 [.。。End With 語句](../../../language-reference/statements/with-end-with-statement.md)。  
  
## <a name="see-also"></a>另請參閱

- [控制流程](index.md)
- [決策結構](decision-structures.md)
- [迴圈結構](loop-structures.md)
- [巢狀控制結構](nested-control-structures.md)
- [Using 語句](../../../language-reference/statements/using-statement.md)
- [With...End With 陳述式](../../../language-reference/statements/with-end-with-statement.md)

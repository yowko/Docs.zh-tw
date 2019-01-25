---
title: '&#39;類別&#39;陳述式必須搭配相對應的結尾&#39;結束類別&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 4e80ce58048bfa7f2fecc65e7167479df07bf57c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715084"
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a>&#39;類別&#39;陳述式必須搭配相對應的結尾&#39;結束類別&#39;
`Class` 用來起始`Class`區塊，因此它只能出現在區塊中，搭配相對應的開頭`End Class`結束區塊的陳述式。 您有多餘`Class`陳述式，或您有未結束您`Class`含有區塊`End Class`。  
  
 **錯誤 ID:** BC30481  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   找到並移除不必要的 `Class` 陳述式。  
  
-   結束`Class`搭配相對應的區塊`End Class`。  
  
## <a name="see-also"></a>另請參閱
- [結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)

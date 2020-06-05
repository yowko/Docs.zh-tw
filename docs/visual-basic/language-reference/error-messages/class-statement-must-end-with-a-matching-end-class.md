---
title: "'Class' 陳述式之後必須搭配相對應的 'End Class'"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 01c231f577d21028e9ef92f37c7ac5f7f1fe2aa3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415384"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a>'Class' 陳述式之後必須搭配相對應的 'End Class'
`Class`是用來起始 `Class` 區塊; 因此，它只能出現在區塊開頭，並以相符 `End Class` 的語句結束區塊。 您有多餘的 `Class` 語句，或尚未 `Class` 使用結束區塊 `End Class` 。  
  
 **錯誤識別碼：** BC30481  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 找到並移除不必要的 `Class` 陳述式。  
  
- 結束 `Class` 具有相符的區塊 `End Class` 。  
  
## <a name="see-also"></a>另請參閱

- [End \<keyword> 語句](../statements/end-keyword-statement.md)
- [Class 陳述式](../statements/class-statement.md)

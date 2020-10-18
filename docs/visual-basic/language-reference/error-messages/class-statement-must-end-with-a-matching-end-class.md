---
title: "'Class' 陳述式之後必須搭配相對應的 'End Class'"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 6889e97aad913f6911ce438892752542de0d10f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163190"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a>BC30481： ' Class ' 語句之後必須搭配相對應的 ' End Class '

`Class` 用來起始 `Class` 區塊; 因此，它只能出現在區塊的開頭，且相符的 `End Class` 語句會結束區塊。 可能是您有多餘的 `Class` 語句，或尚未結束您 `Class` 的區塊 `End Class` 。

 **錯誤識別碼：** BC30481

## <a name="to-correct-this-error"></a>更正這個錯誤

- 找到並移除不必要的 `Class` 陳述式。

- 使用相符的來結束 `Class` 區塊 `End Class` 。

## <a name="see-also"></a>另請參閱

- [End \<keyword> 語句](../statements/end-keyword-statement.md)
- [Class 陳述式](../statements/class-statement.md)

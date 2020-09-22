---
title: 陳述式不能在 'If' 陳述式行之外結束區塊
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 5e75c29e57a9c04c66e6bca79d99bb18c513f667
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870735"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>陳述式不能在 'If' 陳述式行之外結束區塊

單行 `If` 語句包含數個以冒號分隔的語句 (： ) ，其中一個語句是 `End` 單一行以外的控制項區塊語句 `If` 。 單行 `If` 語句不會使用 `End If` 語句。  
  
 **錯誤識別碼：** BC32005  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將單行語句移至 `If` 包含語句的控制項區塊外部 `End If` 。  
  
## <a name="see-also"></a>另請參閱

- [If...Then...Else 陳述式](../statements/if-then-else-statement.md)

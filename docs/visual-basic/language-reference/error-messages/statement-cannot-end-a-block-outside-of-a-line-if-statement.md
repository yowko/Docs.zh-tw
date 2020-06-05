---
title: 陳述式不能在 'If' 陳述式行之外結束區塊
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400314"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>陳述式不能在 'If' 陳述式行之外結束區塊
單行 `If` 語句包含數個以冒號分隔的語句（:)，其中一個是 `End` 單一行外之控制區塊的語句 `If` 。 單行 `If` 語句不會使用 `End If` 語句。  
  
 **錯誤識別碼：** BC32005  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將單行 `If` 語句移出包含語句的控制區塊外 `End If` 。  
  
## <a name="see-also"></a>另請參閱

- [If...Then...Else 陳述式](../statements/if-then-else-statement.md)

---
title: 陳述式不能在 'If' 陳述式行之外結束區塊
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0cee52f0ca00395d93c469aae6498fd3793f1085
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266307"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>陳述式不能在 'If' 陳述式行之外結束區塊
單行`If`陳述式包含的冒號 （:），其中之一就是隔開的多個陳述式`End`單行外控制區塊的陳述式`If`。 單行`If`陳述式不使用`End If`陳述式。  
  
 **錯誤 ID:** BC32005  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移動單行`If`陳述式包含在控制區塊外的`End If`陳述式。  
  
## <a name="see-also"></a>另請參閱
- [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

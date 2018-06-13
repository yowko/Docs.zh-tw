---
title: 陳述式不能在之外結束區塊一條線&#39;如果&#39;陳述式
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596680"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>陳述式不能在之外結束區塊一條線&#39;如果&#39;陳述式
單行`If`陳述式包含以冒號 （:），其中一項分隔的數個陳述式`End`控制區塊之外單行陳述式`If`。 單行`If`陳述式就不會使用`End If`陳述式。  
  
 **錯誤 ID:** BC32005  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移動的單一線條`If`陳述式區塊外部的控制項，其中包含`End If`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [If...Then...Else 陳述式](../../../visual-basic/language-reference/statements/if-then-else-statement.md)

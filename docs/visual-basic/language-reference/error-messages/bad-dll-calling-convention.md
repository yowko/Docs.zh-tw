---
title: 不正確的 DLL 呼叫慣例
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409877"
---
# <a name="bad-dll-calling-convention"></a>不正確的 DLL 呼叫慣例
傳遞至動態連結程式庫（DLL）的引數必須完全符合常式所預期的參數。 呼叫慣例會處理引數的數目、類型和順序。 您的程式可能會在傳遞錯誤類型或引數數目的 DLL 中呼叫常式。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定所有引數類型都與您所呼叫之常式的宣告中指定的是一致的。  
  
2. 請確定您傳遞的引數數目與您呼叫的常式宣告中所指出的數量相同。  
  
3. 如果 DLL 常式預期會以傳值方式引數，請確定 `ByVal` 已針對常式宣告中的這些引數指定。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../programming-guide/language-features/error-types.md)
- [Call 陳述式](../statements/call-statement.md)
- [Declare Statement](../statements/declare-statement.md)

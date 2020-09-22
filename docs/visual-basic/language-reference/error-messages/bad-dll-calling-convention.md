---
title: 不正確的 DLL 呼叫慣例
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 0481bd5e4dfe7a24dff454d0754b519509fa967f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875739"
---
# <a name="bad-dll-calling-convention"></a>不正確的 DLL 呼叫慣例

傳遞至動態連結程式庫 (DLL) 的引數必須完全符合常式所預期的引數。 呼叫慣例會處理數目、類型和引數的順序。 您的程式可能是在傳遞錯誤類型或引數數目的 DLL 中呼叫常式。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定所有引數類型都同意您要呼叫的常式宣告中指定的類型。  
  
2. 請確定您傳遞的引數數目與您要呼叫的常式宣告中所指定的數目相同。  
  
3. 如果 DLL 常式需要以傳值方式引數，請確定 `ByVal` 已針對常式宣告中的那些引數指定。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../programming-guide/language-features/error-types.md)
- [Call 陳述式](../statements/call-statement.md)
- [Declare Statement](../statements/declare-statement.md)

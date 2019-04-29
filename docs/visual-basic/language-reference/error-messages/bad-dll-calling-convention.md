---
title: 不正確的 DLL 呼叫慣例
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935274"
---
# <a name="bad-dll-calling-convention"></a>不正確的 DLL 呼叫慣例
引數傳遞至動態連結程式庫 (DLL) 必須完全符合所預期的常式。 呼叫慣例處理數字、 類型和引數的順序。 您的程式可能會呼叫常式錯誤的類型或數目的引數傳遞的 DLL 中。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定您要呼叫的常式的宣告中所指定同意所有引數類型。  
  
2. 請確定您傳遞您要呼叫的常式的宣告中指定的引數數目相同。  
  
3. 如果 DLL 常式的引數必須為值，請確定`ByVal`指定這些引數的常式的宣告中。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Call 陳述式](../../../visual-basic/language-reference/statements/call-statement.md)
- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)

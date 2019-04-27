---
title: 委派類別 '<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803632"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>委派類別\<類別名稱 >' 已經沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標
呼叫`Invoke`透過委派失敗，因為`Invoke`上委派類別未實作。  
  
 **錯誤 ID:** BC30220  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 確保委派類別的執行個體，已經建立具有`Dim`陳述式和程序已被指派委派執行個體，但`AddressOf`運算子。  
  
2. 找出實作的委派類別的程式碼，並確定它會實作`Invoke`程序。  
  
## <a name="see-also"></a>另請參閱

- [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)

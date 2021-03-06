---
title: 委派類別 '<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 4e0fc61c7356008755134f670fa1fab0165cfd48
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162787"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>BC30220：委派類別 ' \<classname> ' 沒有 Invoke 方法，因此這個類型的運算式不可以是方法呼叫的目標

`Invoke`透過委派的呼叫失敗，因為未 `Invoke` 在委派類別上執行。

 **錯誤識別碼：** BC30220

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 確定已使用語句建立委派類別的實例 `Dim` ，而且已使用運算子將程式指派給委派實例 `AddressOf` 。

2. 找出可執行委派類別的程式碼，並確定它會執行程式 `Invoke` 。

## <a name="see-also"></a>另請參閱

- [委派](../../programming-guide/language-features/delegates/index.md)
- [Delegate 陳述式](../statements/delegate-statement.md)
- [AddressOf 運算子](../operators/addressof-operator.md)
- [Dim 陳述式](../statements/dim-statement.md)

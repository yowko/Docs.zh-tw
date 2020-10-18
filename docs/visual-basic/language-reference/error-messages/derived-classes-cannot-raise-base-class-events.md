---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 7b86420466d77a6aa45b1201a9375b4433e4b5ec
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163437"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a>BC30029：衍生的類別無法引發基類事件

事件只能從宣告的宣告空間引發。 因此，類別無法從任何其他類別（甚至是衍生的類別）引發事件。

 **錯誤識別碼：** BC30029

## <a name="to-correct-this-error"></a>更正這個錯誤

- 移動 `Event` 語句或 `RaiseEvent` 語句，使其位於相同的類別中。

## <a name="see-also"></a>另請參閱

- [Event 陳述式](../statements/event-statement.md)
- [RaiseEvent 陳述式](../statements/raiseevent-statement.md)

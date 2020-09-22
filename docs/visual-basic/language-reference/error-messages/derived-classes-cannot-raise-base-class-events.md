---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0233a1584c5e871506b5c4762e98874c343f19b8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874485"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>衍生的類別無法引發基底類別事件

事件只能從宣告的宣告空間引發。 因此，類別無法從任何其他類別（甚至是衍生的類別）引發事件。  
  
 **錯誤識別碼：** BC30029  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 移動 `Event` 語句或 `RaiseEvent` 語句，使其位於相同的類別中。  
  
## <a name="see-also"></a>另請參閱

- [Event 陳述式](../statements/event-statement.md)
- [RaiseEvent 陳述式](../statements/raiseevent-statement.md)

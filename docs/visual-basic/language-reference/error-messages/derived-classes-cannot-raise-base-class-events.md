---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409695"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>衍生的類別無法引發基底類別事件
事件只能從其宣告所在的宣告空間引發。 因此，類別無法從任何其他類別引發事件，甚至是衍生自它的來源。  
  
 **錯誤識別碼：** BC30029  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 移動 `Event` 語句或 `RaiseEvent` 語句，使其位於相同的類別中。  
  
## <a name="see-also"></a>另請參閱

- [Event 陳述式](../statements/event-statement.md)
- [RaiseEvent 陳述式](../statements/raiseevent-statement.md)

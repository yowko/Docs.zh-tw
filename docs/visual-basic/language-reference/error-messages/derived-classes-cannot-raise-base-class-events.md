---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 030c9c2ffa97572298b23f05c23e3af0df7387b0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913166"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>衍生的類別無法引發基底類別事件
只能從其宣告的宣告空間，就可以引發事件。 因此，類別無法引發任何其他類別，即使其中從中衍生的事件。  
  
 **錯誤 ID:** BC30029  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 移動`Event`陳述式或`RaiseEvent`陳述式，使它們位於相同的類別。  
  
## <a name="see-also"></a>另請參閱

- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md)

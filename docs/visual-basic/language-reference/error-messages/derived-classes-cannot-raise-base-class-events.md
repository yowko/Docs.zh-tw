---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0e9acf4b3e71295655c15ae9b1c80852c9aca8df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803567"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>衍生的類別無法引發基底類別事件
只能從其宣告的宣告空間，就可以引發事件。 因此，類別無法引發任何其他類別，即使其中從中衍生的事件。  
  
 **錯誤 ID:** BC30029  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 移動`Event`陳述式或`RaiseEvent`陳述式，使它們位於相同的類別。  
  
## <a name="see-also"></a>另請參閱

- [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)
- [RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md)

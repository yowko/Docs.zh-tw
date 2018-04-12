---
title: 衍生的類別無法引發基底類別事件
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>衍生的類別無法引發基底類別事件
只能從宣告它的宣告空間，可以引發事件。 因此，類別無法引發任何其他類別，即使其中從中衍生的事件。  
  
 **錯誤 ID:** BC30029  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   移動`Event`陳述式或`RaiseEvent`陳述式，使它們位於相同的類別。  
  
## <a name="see-also"></a>另請參閱  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md)

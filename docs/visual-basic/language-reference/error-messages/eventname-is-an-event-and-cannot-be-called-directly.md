---
title: "'<eventname>' 是個事件，不可直接呼叫"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: bf900566bdb4ecf8d8961a12b5dd67ba426caf27
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305594"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>'\<事件名稱 >' 是個事件，並不能直接呼叫
' <`eventname`>' 是個事件，並因此無法直接呼叫。 使用`RaiseEvent`陳述式來引發事件。  
  
 程序呼叫指定的程序名稱的事件。 事件處理常式是程序，但事件本身發出訊號的裝置，它必須引發並處理。  
  
 **錯誤 ID:** BC32022  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用`RaiseEvent`陳述式來對事件發出信號，並叫用程序或處理程序。  
  
## <a name="see-also"></a>另請參閱

- [RaiseEvent 陳述式](../../../visual-basic/language-reference/statements/raiseevent-statement.md)

---
title: "'<eventname>' 是個事件，不可直接呼叫"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 3366bc215a45cd7de9dc2de285758a78144df509
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874321"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>'\<eventname>' 是個事件，不可直接呼叫

「<`eventname`>」是事件，所以無法直接呼叫。 使用 `RaiseEvent` 語句來引發事件。  
  
 程序呼叫會指定程式名稱的事件。 事件處理常式是一種程式，但事件本身是必須引發和處理的信號裝置。  
  
 **錯誤識別碼：** BC32022  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用 `RaiseEvent` 語句來發出事件的信號，並叫用處理它的程式或程式。  
  
## <a name="see-also"></a>另請參閱

- [RaiseEvent 陳述式](../statements/raiseevent-statement.md)

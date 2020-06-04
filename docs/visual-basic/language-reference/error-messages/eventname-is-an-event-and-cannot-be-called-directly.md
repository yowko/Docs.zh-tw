---
title: "'<eventname>' 是個事件，不可直接呼叫"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 510fff5370e63a31ee271421c0ab6f154518899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409591"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a>'\<eventname>' 是個事件，不可直接呼叫
「<`eventname`>」是事件，因此無法直接呼叫。 使用 `RaiseEvent` 語句來引發事件。  
  
 程序呼叫會指定程式名稱的事件。 事件處理常式是一種程式，但事件本身是信號裝置，必須加以引發和處理。  
  
 **錯誤識別碼：** BC32022  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 使用 `RaiseEvent` 語句來通知事件，並叫用處理它的程式。  
  
## <a name="see-also"></a>另請參閱

- [RaiseEvent 陳述式](../statements/raiseevent-statement.md)

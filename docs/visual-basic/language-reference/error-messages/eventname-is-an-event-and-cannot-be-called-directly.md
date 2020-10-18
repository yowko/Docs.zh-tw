---
title: "'<eventname>' 是個事件，不可直接呼叫"
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 246cb92daa2c838c95f695542f33cf02af42764d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161981"
---
# <a name="bc32022-eventname-is-an-event-and-cannot-be-called-directly"></a>BC32022： ' \<eventname> ' 是事件，無法直接呼叫

「<`eventname`>」是事件，所以無法直接呼叫。 使用 `RaiseEvent` 語句來引發事件。

 程序呼叫會指定程式名稱的事件。 事件處理常式是一種程式，但事件本身是必須引發和處理的信號裝置。

 **錯誤識別碼：** BC32022

## <a name="to-correct-this-error"></a>更正這個錯誤

- 使用 `RaiseEvent` 語句來發出事件的信號，並叫用處理它的程式或程式。

## <a name="see-also"></a>另請參閱

- [RaiseEvent 陳述式](../statements/raiseevent-statement.md)

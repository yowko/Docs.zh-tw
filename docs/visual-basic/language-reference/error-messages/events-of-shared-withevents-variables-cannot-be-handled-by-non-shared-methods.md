---
title: 共用 WithEvents 變數的事件不能由非共用的方法處理
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409565"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共用 WithEvents 變數的事件不能由非共用的方法處理
使用修飾詞宣告的變數 `Shared` 是共用變數。 共用變數只會識別一個儲存位置。 以修飾詞宣告的變數 `WithEvents` 會判斷變數所屬的類型會處理變數所引發之事件的集合。 將值指派給變數時，宣告所建立的屬性會解除與 `WithEvents` 任何現有的事件處理常式的連結，並透過方法來連結新的事件處理常式 `Add` 。  
  
 **錯誤識別碼：** BC30594  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 宣告您的事件處理常式 `Shared` 。  
  
## <a name="see-also"></a>另請參閱

- [共用][](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)

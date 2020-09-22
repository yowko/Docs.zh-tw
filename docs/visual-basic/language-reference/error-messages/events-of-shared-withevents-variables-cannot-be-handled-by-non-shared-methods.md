---
title: 共用 WithEvents 變數的事件不能由非共用的方法處理
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: d519463e036de215143efad5be3745484ac17d82
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874296"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>共用 WithEvents 變數的事件不能由非共用的方法處理

使用修飾詞宣告的變數 `Shared` 是共用變數。 共用變數只會識別一個儲存位置。 以修飾詞宣告的變數會判斷提示 `WithEvents` 所屬的類型會處理變數所引發的事件集。 將值指派給變數時，宣告所建立的屬性會解除 `WithEvents` 所有現有的事件處理常式的連結，並透過方法連結新的事件處理常式 `Add` 。  
  
 **錯誤識別碼：** BC30594  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 宣告您的事件處理常式 `Shared` 。  
  
## <a name="see-also"></a>另請參閱

- [共用][](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)

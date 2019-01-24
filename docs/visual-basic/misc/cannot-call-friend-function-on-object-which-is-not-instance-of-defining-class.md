---
title: 無法在不是定義類別執行個體的物件上呼叫 Friend 函式
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a107b2a11f6f8324c3029e83c5eca64c2ee32ebf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742827"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>無法在不是定義類別執行個體的物件上呼叫 Friend 函式
可能是您嘗試呼叫類別的 `Friend` 程序，或嘗試存取跨處理序或跨執行緒的 `Friend` 屬性或方法。 `Friend` 程序可以從類別外部的模組呼叫，但其為已定義類別之專案的一部分。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   確定您從屬於已定義類別之專案的模組，呼叫或存取程序。  
  
## <a name="see-also"></a>另請參閱
- [Friend](../../visual-basic/language-reference/modifiers/friend.md)

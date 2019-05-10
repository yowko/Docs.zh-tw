---
title: 無法在不是定義類別執行個體的物件上呼叫 Friend 函式
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a227e5761bacc36c0682844a833e70c34582a5d3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622599"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>無法在不是定義類別執行個體的物件上呼叫 Friend 函式
可能是您嘗試呼叫類別的 `Friend` 程序，或嘗試存取跨處理序或跨執行緒的 `Friend` 屬性或方法。 `Friend` 程序可以從類別外部的模組呼叫，但其為已定義類別之專案的一部分。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 確定您從屬於已定義類別之專案的模組，呼叫或存取程序。  
  
## <a name="see-also"></a>另請參閱

- [Friend](../../visual-basic/language-reference/modifiers/friend.md)

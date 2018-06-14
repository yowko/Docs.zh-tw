---
title: 建構函式&#39;&lt;名稱&gt;&#39;不能呼叫自己本身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 069de813a0426230e19cddf14c3b83d40a602a41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588992"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a>建構函式&#39;&lt;名稱&gt;&#39;不能呼叫自己本身
A`Sub New`類別或結構中的程序呼叫本身。  
  
 建構函式的目的是要初始化類別的執行個體，或建立結構時第一次。 類別或結構可以有數個建構函式，前提是它們都有不同的參數清單。 建構函式可以呼叫其他建構函式，以執行其功能，除了它自己。 它是無意義的建構函式呼叫其本身，但事實上這會導致無限遞迴如果允許。  
  
 **錯誤 ID:** BC30298  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查所呼叫的建構函式的參數清單。 它應該是不同的建構函式進行呼叫。  
  
2.  如果您不想呼叫不同的建構函式，移除`Sub New`完全呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [物件存留期：物件的建立和終結](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

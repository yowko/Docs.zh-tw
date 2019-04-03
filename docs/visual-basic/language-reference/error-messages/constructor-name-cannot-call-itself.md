---
title: 建構函式 '<name>' 不能呼叫自己本身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: ef20f74055a07071ef9634973c6852ac58c3143c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824703"
---
# <a name="constructor-name-cannot-call-itself"></a>建構函式 '\<名稱 >' 不可呼叫其本身
A`Sub New`類別或結構中的程序呼叫本身。  
  
 建構函式的目的是要初始化類別的執行個體，或建立結構時第一次。 類別或結構可以有數個建構函式，前提是它們都有不同的參數清單。 建構函式可以呼叫其他建構函式，以執行其功能，除了它自己。 但是這樣做沒有意義的建構函式呼叫本身，而且事實上這會導致無限遞迴如果允許。  
  
 **錯誤 ID:** BC30298  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請檢查建構函式所呼叫的參數清單。 它應該是不同的建構函式進行呼叫。  
  
2.  如果您不想呼叫不同的建構函式，移除`Sub New`完全呼叫。  
  
## <a name="see-also"></a>另請參閱

- [物件存留期：如何建立和終結物件](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

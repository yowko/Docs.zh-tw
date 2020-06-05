---
title: 建構函式 '<name>' 不能呼叫自己本身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409799"
---
# <a name="constructor-name-cannot-call-itself"></a>建構函式 '\<name>' 不能呼叫自己本身
`Sub New`類別或結構中的程式會呼叫本身。  
  
 函式的用途是在第一次建立類別或結構時，初始化它的實例。 類別或結構可以有數個函式，但前提是它們都有不同的參數清單。 除了它自己的功能之外，還允許使用一個函式來呼叫另一個函式來執行其功能。 但是，對函式而言，呼叫本身並沒有任何意義，事實上，如果允許，則會導致無限遞迴。  
  
 **錯誤識別碼：** BC30298  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請檢查所呼叫之函式的參數清單。 它應該與進行呼叫的函式不同。  
  
2. 如果您不想要呼叫不同的函式，請 `Sub New` 完全移除呼叫。  
  
## <a name="see-also"></a>另請參閱

- [物件存留期：物件的建立和終結](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)

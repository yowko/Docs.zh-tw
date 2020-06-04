---
title: 前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397320"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現
不在區塊內的句號（.）或驚嘆號（！）不會 `With` 出現在左邊的運算式。 成員存取（ `.` ）和字典成員存取（ `!` ）需要一個運算式來指定包含該成員的元素。 這必須立即出現在存取子的左邊，或做為 `With` 包含成員存取之區塊的目標。  
  
 **錯誤識別碼：** BC30157  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定 `With` 已正確地格式化區塊。  
  
2. 如果沒有 `With` 區塊，請在存取子的左邊加上運算式，以評估為包含該成員的已定義元素。  
  
## <a name="see-also"></a>另請參閱

- [程式碼中的特殊字元](../../programming-guide/program-structure/special-characters-in-code.md)
- [With...End With 陳述式](../statements/with-end-with-statement.md)

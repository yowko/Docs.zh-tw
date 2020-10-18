---
title: 前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 4ff273d5930fe58a5bccf0f4f4c10e971d777d01
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162501"
---
# <a name="bc30157-leading--or--can-only-appear-inside-a-with-statement"></a>BC30157：前置的 '. ' 或 '！ ' 只可以在 ' With ' 語句中出現

不在區塊內的句點 (. ) 或驚嘆號 (！ ) 不會 `With` 出現在左邊的運算式。 成員存取 (`.`) 和字典成員存取 (`!`) 需要指定包含成員之元素的運算式。 這必須緊接在存取子的左邊，或做為 `With` 包含成員存取之區塊的目標。

 **錯誤識別碼：** BC30157

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 確定區塊的 `With` 格式正確。

2. 如果沒有 `With` 區塊，請在存取子的左邊加入一個運算式，此運算式會評估為包含該成員的定義專案。

## <a name="see-also"></a>另請參閱

- [程式碼中的特殊字元](../../programming-guide/program-structure/special-characters-in-code.md)
- [With...End With 陳述式](../statements/with-end-with-statement.md)

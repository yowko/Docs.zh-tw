---
title: 索引數目超過索引陣列維度的數目
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 9a191ff7ec3ad6a607e6509cc143c359f64f21ea
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159907"
---
# <a name="bc30106-number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>BC30106：索引數目超過索引陣列的維度數目

用來存取陣列項目的索引數目必須與陣列的陣序 (也就是為其宣告的維度數目) 完全相同。

 **錯誤識別碼：** BC30106

## <a name="to-correct-this-error"></a>更正這個錯誤

- 移除陣列參考中的注標，直到下標總數等於陣列的順位。 例如：

    ```vb
    Dim gameBoard(3, 3) As String

    ' Incorrect code. The array has two dimensions.
    gameBoard(1, 1, 1) = "X"
    gameBoard(2, 1, 1) = "O"

    ' Correct code.
    gameBoard(0, 0) = "X"
    gameBoard(1, 0) = "O"
    ```

## <a name="see-also"></a>另請參閱

- [陣列](../../programming-guide/language-features/arrays/index.md)

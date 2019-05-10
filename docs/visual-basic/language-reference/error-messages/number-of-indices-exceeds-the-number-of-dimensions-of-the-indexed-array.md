---
title: 索引數目超過索引陣列維度的數目
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 76cf0a997e9ad36ab4b5dfdc7c4bc29c57d309eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665697"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a>索引數目超過索引陣列維度的數目
用來存取陣列項目的索引數目必須與陣列的陣序 (也就是為其宣告的維度數目) 完全相同。  
  
 **錯誤 ID:** BC30106  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 直到註標的總數等於陣列的陣序規範，則您可以移除陣列參考註標。 例如:   
  
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

- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)

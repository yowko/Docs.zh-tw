---
title: 陣列界限的宣告不可以出現在類型規範中
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 951f710160ae1023671773c21c73946f5ae94c2b
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512767"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>陣列界限的宣告不可以出現在類型規範中

陣列大小不能宣告為資料類型規範的一部分。

**錯誤識別碼:** BC30638

## <a name="to-correct-this-error"></a>更正這個錯誤

- 指定緊接在變數名稱後面的陣列大小, 而不是將陣列大小放在類型後面, 如下列範例所示。

  ```vb
  Dim Array(8) As Integer
  ```

- 定義陣列, 並使用所需的元素數目將它初始化, 如下列範例所示。

  ```vb
  Dim Array2() As Integer = New Integer(8) {}
  ```

## <a name="see-also"></a>另請參閱

- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)

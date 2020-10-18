---
title: "'Is' 需要有參考類型的運算元，但此運算元擁有實值類型 '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163346"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a>BC30020： ' Is ' 需要有參考型別的運算元，但此運算元的數值型別為 ' \<typename> '

`Is`比較運算子會判斷兩個物件變數是否參考相同的實例。 未針對實數值型別定義這項比較。

 **錯誤識別碼：** BC30020

## <a name="to-correct-this-error"></a>更正這個錯誤

- 使用適當的算術比較運算子或 `Like` 運算子來比較兩個實數值型別。

## <a name="see-also"></a>另請參閱

- [Is 運算子](../operators/is-operator.md)
- [Like 運算子](../operators/like-operator.md)
- [比較運算子](../operators/comparison-operators.md)

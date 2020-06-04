---
title: "'Is' 需要有參考類型的運算元，但此運算元擁有實值類型 '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: e5acc94a3738fca3a43740bdba727fc843132aa1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402807"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a>'Is' 需要有參考類型的運算元，但此運算元擁有實值類型 '\<typename>'
`Is`比較運算子會判斷兩個物件變數是否參考相同的實例。 這種比較不會針對實值型別定義。  
  
 **錯誤識別碼：** BC30020  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用適當的算術比較運算子或 `Like` 運算子來比較兩個實數值型別。  
  
## <a name="see-also"></a>另請參閱

- [Is 運算子](../operators/is-operator.md)
- [Like 運算子](../operators/like-operator.md)
- [比較運算子](../operators/comparison-operators.md)

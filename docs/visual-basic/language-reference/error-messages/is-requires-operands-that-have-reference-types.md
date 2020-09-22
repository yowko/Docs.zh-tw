---
title: "'Is' 需要有參考類型的運算元，但此運算元擁有實值類型 '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: daf9724fef81b4d7adb4f571ee950723aec09d8d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873907"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a>'Is' 需要有參考類型的運算元，但此運算元擁有實值類型 '\<typename>'

`Is`比較運算子會判斷兩個物件變數是否參考相同的實例。 未針對實數值型別定義這項比較。  
  
 **錯誤識別碼：** BC30020  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用適當的算術比較運算子或 `Like` 運算子來比較兩個實數值型別。  
  
## <a name="see-also"></a>另請參閱

- [Is 運算子](../operators/is-operator.md)
- [Like 運算子](../operators/like-operator.md)
- [比較運算子](../operators/comparison-operators.md)

---
title: 數值與比較運算子
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: b29f78a13d6d0313e0ad29754f6d13ac08be1092
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783132"
---
# <a name="numeric-and-comparison-operators"></a>數值與比較運算子

除了下列幾點以外，在 Common Language Runtime (CLR) 中算術和比較運算子都會如預期運作：

- SQL 不支援浮點數值 (Floating-Point Number) 的模數運算子。

- SQL 不支援不檢查的算術。

- 當您在無法於 SQL 中複寫因而不受支援的運算式中使用遞增和遞減運算子時，這些運算子會造成副作用。

## <a name="supported-operators"></a>支援的運算子

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援下列運算子。

- 基本算術運算子：

  - `+`

  - `-` (減法)

  - `*`

  - `/`

  - Visual Basic 整數除法 (`\`)

  - `%` (Visual Basic `Mod`)

  - `<<`

  - `>>`

  - `-` (一元否定運算)

- 基本比較運算子：

  - Visual Basic `=` 和 C# `==`

  - Visual Basic `<>` 和 C# `!=`

  - Visual Basic `Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>另請參閱

- [資料類型和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [C# 運算子](../../../../../../docs/csharp/language-reference/operators/index.md)
- [運算子](../../../../../visual-basic/language-reference/operators/index.md)

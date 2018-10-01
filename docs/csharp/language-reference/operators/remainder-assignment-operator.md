---
title: '%= 運算子 (C# 參考)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085636"
---
# <a name="-operator-c-reference"></a>%= 運算子 (C# 參考)

餘數指派運算子。

使用 `%=` 運算子的運算式，例如  

```csharp
x %= y
```  

相當於  

```csharp
x = x % y
```  

但只會評估 `x` 一次。
  
所有數字類型都支援[餘數運算子](remainder-operator.md) `%`，並在除以其運算元後計算餘數。

如果使用者定義型別[多載](../keywords/operator.md)[餘數運算子](remainder-operator.md) `%`，餘數指派運算子 `%=` 會隱含多載。
  
下列範例示範 `%=` 運算子的用法：

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)

---
title: 衍生的數學函式
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: f84b1ef18ef2a924bb2e47da85ecbb51f982873a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869018"
---
# <a name="derived-math-functions-visual-basic"></a>衍生的數學函式 (Visual Basic)

下表顯示的非內建數學函數，可以衍生自物件的內建數學函數 <xref:System.Math?displayProperty=nameWithType> 。 您可以藉由加入至您的檔案 `Imports System.Math` 或專案來存取內建數學函數。  
  
|函式|衍生的對應專案|  
|--------------|-------------------------|  
|正割 (Sec (x) # A3|1/Cos (x) |  
| (Csc (x) # A3 的余割|1/Sin (x) |  
|餘切 (Ctan (x) # A3|1/Tan (x) |  
|反向正弦 (Asin (x) # A3|Atan (x/Sqrt (-x * x + 1) # A3|  
|反向余弦 (Acos (x) # A3|Atan (-x/Sqrt (-x * x + 1) # A3 + 2 \* Atan (1) |  
|反向正向 (Asec (x) # A3|2 * Atan (1) – Atan (Sign (x) /Sqrt (x \* x – 1) # A7|  
|反向余割 (Acsc (x) # A3|Atan (Sign (x) /Sqrt (x * x – 1) # A5|  
|反向餘切 (Acot (x) # A3|2 * Atan (1) -Atan (x) |  
|雙曲正弦 (Sinh (x) # A3| (Exp (x) – Exp (-x) # A5/2|  
|雙曲余弦 (Cosh (x) # A3| (Exp (x) + Exp (-x) # A5/2|  
|雙曲正切函數 (Tanh (x) # A3| (Exp (x) – Exp (-x) # A5/ (Exp (x) + Exp (-x) # A11|  
|雙曲正割 (Sech (x) # A3|2/ (Exp (x) + Exp (-x) # A5|  
|雙曲余割 (Csch (x) # A3|2/ (Exp (x) – Exp (-x) # A5|  
|雙曲餘切 (Coth (x) # A3| (Exp (x) + Exp (-x) # A5/ (Exp (x) – Exp (-x) # A11|  
|反向雙曲正弦 (Asinh (x) # A3|Log (x + Sqrt (x * x + 1) # A3|  
|反向雙曲余弦 (Acosh (x) # A3|Log (x + Sqrt (x * x – 1) # A3|  
|反向雙曲正切函數 (Atanh (x) # A3|Log ( # B1 1 + x) / (1 – x) # A5/2|  
|反向雙曲正割 (AsecH (x) # A3|Log ( # B1 Sqrt (-x * x + 1) + 1) /x) |  
|反向雙曲余割 (Acsch (x) # A3|Log ( # B1 Sign (x) * Sqrt (x \* x + 1) + 1) /x) |  
|反向雙曲餘切 (Acoth (x) # A3|Log ( # B1 x + 1) / (x – 1) # A5/2|  
  
## <a name="see-also"></a>另請參閱

- [數學函式](../functions/math-functions.md)

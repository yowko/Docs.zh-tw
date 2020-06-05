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
ms.openlocfilehash: 611f3d8faf2148b8a983467d9ace4fd6c18b30e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373876"
---
# <a name="derived-math-functions-visual-basic"></a>衍生的數學函式 (Visual Basic)
下表顯示的非內建數學函數，可以衍生自物件的內建數學函式 <xref:System.Math?displayProperty=nameWithType> 。 您可以藉由將加入至您的檔案或專案，來存取內建的數學函數 `Imports System.Math` 。  
  
|函式|衍生的對等專案|  
|--------------|-------------------------|  
|正割（秒（x））|1/Cos （x）|  
|余割（Csc （x））|1/Sin （x）|  
|餘切（Ctan （x））|1/Tan （x）|  
|反正弦函數（Asin （x））|Atan （x/Sqrt （-x * x + 1））|  
|反余弦函數（Acos （x））|Atan （-x/Sqrt （-x * x + 1）） + 2 \* Atan （1）|  
|反正割（Asec （x））|2 * Atan （1）– Atan （Sign （x）/Sqrt （x \* x –1））|  
|反向余割（Acsc （x））|Atan （Sign （x）/Sqrt （x * x –1））|  
|反向餘切（Acot （x））|2 * Atan （1）-Atan （x）|  
|雙曲正弦（Sinh （x））|（Exp （x）– Exp （-x））/2|  
|雙曲余弦（Cosh （x））|（Exp （x） + Exp （-x））/2|  
|雙曲正切函數（Tanh （x））|（Exp （x）– Exp （-x））/（Exp （x） + Exp （-x））|  
|雙曲正割（Sech （x））|2/（Exp （x） + Exp （-x））|  
|雙曲余割（Csch （x））|2/（Exp （x）– Exp （-x））|  
|雙曲餘切（Coth （x））|（Exp （x） + Exp （-x））/（Exp （x）– Exp （-x））|  
|反雙曲正弦（Asinh （x））|Log （x + Sqrt （x * x + 1））|  
|反雙曲余弦（Acosh （x））|Log （x + Sqrt （x * x –1））|  
|反雙曲正切（Atanh （x））|Log （（1 + x）/（1– x））/2|  
|反雙曲正割（AsecH （x））|Log （（Sqrt （-x * x + 1） + 1）/x）|  
|反雙曲余割（Acsch （x））|Log （（符號（x） * Sqrt （x \* x + 1） + 1）/x）|  
|反雙曲餘切（Acoth （x））|Log （（x + 1）/（x –1））/2|  
  
## <a name="see-also"></a>另請參閱

- [Math 函數](../functions/math-functions.md)

---
title: "衍生的數學函式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5816fa4c8c384eca116fa1512950a3588c6e3392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="derived-math-functions-visual-basic"></a>衍生的數學函式 (Visual Basic)
下表顯示這些可以衍生自內建數學函式的非內建的數學函式<xref:System.Math?displayProperty=nameWithType>物件。 您可以存取內建數學函式加入`Imports System.Math`至您的檔案或專案。  
  
|函式|在衍生的對等項目|  
|--------------|-------------------------|  
|正割 (Sec(x))|1 / Cos(x)|  
|餘割 (Csc(x))|1 / Sin(x)|  
|餘切函數 (Ctan(x))|1 / Tan(x)|  
|反正弦 (Asin(x))|Atan (x / Sqrt (-x * x + 1))|  
|反餘弦 (Acos(x))|Atan (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)|  
|反向正割 (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x – 1))|  
|數值的反餘割 (Acsc(x))|Atan(Sign(x) / Sqrt (x * x – 1))|  
|數值的反餘切函數 (Acot(x))|2 * Atan(1)-Atan(x)|  
|雙曲線正弦函數 (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|雙曲線餘弦 (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|雙曲正切 (Tanh(x))|(Exp(x) – Exp(-x)) / （Exp(x) + Exp(-x))|  
|雙曲正割 (Sech(x))|2 / （Exp(x) + Exp(-x))|  
|雙曲餘割 (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|雙曲餘切值 (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|反雙曲正弦 (Asinh(x))|記錄檔 (x + Sqrt (x * x + 1))|  
|反雙曲線餘弦 (Acosh(x))|記錄檔 (x + Sqrt (x * x – 1))|  
|反雙曲正切 (Atanh(x))|記錄 ((1 + x) / (1-x)) / 2|  
|數值的反雙曲正割 (AsecH(x))|記錄檔 ((Sqrt (-x * x + 1) + 1) / x)|  
|數值的反雙曲餘割 (Acsch(x))|Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)|  
|數值的反雙曲餘切值 (Acoth(x))|記錄 ((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>另請參閱  
 [數學函式](../../../visual-basic/language-reference/functions/math-functions.md)

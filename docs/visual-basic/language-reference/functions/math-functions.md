---
title: 數學函式
ms.date: 01/27/2020
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: ea30ae3b30484c1a13d6d540f121c03afb30ba26
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794600"
---
# <a name="math-functions-visual-basic"></a>數學函式 (Visual Basic)

<xref:System.Math?displayProperty=nameWithType> 類別的方法會提供三角、對數和其他一般數學函數。

## <a name="remarks"></a>備註

下表列出 <xref:System.Math?displayProperty=nameWithType> 類別的方法。 您可以在 Visual Basic 程式中使用這些功能：
  
|.NET 方法|描述|
|---------------------------|-----------------|
|<xref:System.Math.Abs%2A>|傳回數字的絕對值。|
|<xref:System.Math.Acos%2A>|傳回餘弦函數 (Cosine) 是指定數字的角。|
|<xref:System.Math.Asin%2A>|傳回正弦函數 (Sine) 是指定數字的角。|
|<xref:System.Math.Atan%2A>|傳回正切函數 (Tangent) 是指定數字的角。|
|<xref:System.Math.Atan2%2A>|傳回正切函數是兩個指定數字之商數的角。|
|<xref:System.Math.BigMul%2A>|傳回 2 32 位數位的完整產品。|
|<xref:System.Math.Ceiling%2A>|傳回大於或等於指定 `Decimal` 或 `Double`的最小整數值。|
|<xref:System.Math.Cos%2A>|傳回指定角的餘弦函數。|
|<xref:System.Math.Cosh%2A>|傳回指定角的雙曲線餘弦函數。|
|<xref:System.Math.DivRem%2A>|傳回 2 32 位或64位帶正負號整數的商，同時傳回輸出參數中的餘數。|
|<xref:System.Math.Exp%2A>|傳回指定乘冪的 e （自然對數的底數）。|
|<xref:System.Math.Floor%2A>|傳回小於或等於指定 `Decimal` 或 `Double` 數位的最大整數。|
|<xref:System.Math.IEEERemainder%2A>|傳回指定數位除以另一個指定數位所得的餘數。|
|<xref:System.Math.Log%2A>|傳回指定數位的自然（以 e 為底數）對數，或指定之基底中指定數位的對數。|
|<xref:System.Math.Log10%2A>|傳回指定數字的以 10 為底數的對數。|
|<xref:System.Math.Max%2A>|傳回兩個數字中較大的一個。|
|<xref:System.Math.Min%2A>|傳回兩個數字中較小的一個。|
|<xref:System.Math.Pow%2A>|傳回具有指定乘冪數的指定數字。|
|<xref:System.Math.Round%2A>|傳回 `Decimal` 或 `Double` 值，舍入到最接近的整數值或指定的小數位數。|
|<xref:System.Math.Sign%2A>|傳回 `Integer` 值，表示數位的正負號。|
|<xref:System.Math.Sin%2A>|傳回指定角的正弦函數。|
|<xref:System.Math.Sinh%2A>|傳回指定角的雙曲線正弦函數。|
|<xref:System.Math.Sqrt%2A>|傳回指定數字的平方根。|
|<xref:System.Math.Tan%2A>|傳回指定角的正切函數。|
|<xref:System.Math.Tanh%2A>|傳回指定角的雙曲線正切函數。|
|<xref:System.Math.Truncate%2A>|計算指定 `Decimal` 或 `Double` 數位的整數部分。|

下表列出 .NET Framework 但新增 .NET Standard 或 .NET Core 中 <xref:System.Math?displayProperty=nameWithType> 類別的方法：

|.NET 方法|描述|提供于|
|---------------------------|-----------------|-----------|
|<xref:System.Math.Acosh%2A>|傳回雙曲線餘弦函數是指定數字的角。|從 .NET Core 2.1 和 .NET Standard 2.1 開始|
|<xref:System.Math.Asinh%2A>|傳回雙曲線正弦函數是指定數字的角。|從 .NET Core 2.1 和 .NET Standard 2.1 開始|
|<xref:System.Math.Atanh%2A>|傳回雙曲線正弦函數是指定數字的角。|從 .NET Core 2.1 和 .NET Standard 2.1 開始|
|<xref:System.Math.BitDecrement%2A>|傳回下一個比 `x` 小的最小值。|從 .NET Core 3.0 開始|
|<xref:System.Math.BitIncrement%2A>|傳回下一個比 `x` 大的最大值。|從 .NET Core 3.0 開始|
|<xref:System.Math.Cbrt%2A>|傳回指定數字的立方根。|從 .NET Core 2.1 和 .NET Standard 2.1 開始|
|<xref:System.Math.Clamp%2A>|傳回限制為 `min` 和 `max` 內含範圍的 `value`。|從 .NET Core 2.0 和 .NET Standard 2.1 開始|
|<xref:System.Math.CopySign%2A>|傳回量級為 `x` 且符號為 `y` 的值。|從 .NET Core 3.0 開始|
|<xref:System.Math.FusedMultiplyAdd%2A>|傳回（x \* y） + z，四捨五入為一個三元運算。|從 .NET Core 3.0 開始|
|<xref:System.Math.ILogB%2A>|傳回以 2 為底數時指定數字的整數對數。|從 .NET Core 3.0 開始|
|<xref:System.Math.Log2%2A>|傳回以 2 為底數時指定數字的對數。|從 .NET Core 3.0 開始|
|<xref:System.Math.MaxMagnitude%2A>|傳回兩個雙精確度浮點數中較大的那個量級。|從 .NET Core 3.0 開始|
|<xref:System.Math.MinMagnitude%2A>|傳回兩個雙精確度浮點數中較小的那個量級。|從 .NET Core 3.0 開始|
|<xref:System.Math.ScaleB%2A>|傳回 x \* 2 ^ n，以有效率的方式計算。|從 .NET Core 3.0 開始|

若要在未限定的情況下使用這些函式，請將下列程式碼新增至原始程式檔的頂端，以將 <xref:System.Math?displayProperty=nameWithType> 命名空間匯入至您的專案：

```vb
Imports System.Math
```

## <a name="example---abs"></a>範例-Abs

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Abs%2A> 方法來計算數位的絕對值。

```vb
Dim x As Double = Math.Abs(50.3)
Dim y As Double = Math.Abs(-50.3)
Console.WriteLine(x)
Console.WriteLine(y)
' This example produces the following output:
' 50.3
' 50.3
```  

## <a name="example---atan"></a>範例-Atan

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Atan%2A> 方法來計算 pi 的值。

```vb
Public Function GetPi() As Double
    ' Calculate the value of pi.
    Return 4.0 * Math.Atan(1.0)
End Function
```

> [!NOTE]
> <xref:System.Math?displayProperty=nameWithType> 類別包含 <xref:System.Math.PI?displayProperty=nameWithType> 常數位段。 您可以使用它，而不是計算它。

## <a name="example---cos"></a>範例-Cos

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Cos%2A> 方法來傳回角度的余弦值。

```vb
Public Function Sec(angle As Double) As Double
    ' Calculate the secant of angle, in radians.
    Return 1.0 / Math.Cos(angle)
End Function
```

## <a name="example---exp"></a>範例-Exp

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Exp%2A> 方法，將 e 次方傳回給乘冪。

```vb
Public Function Sinh(angle As Double) As Double
    ' Calculate hyperbolic sine of an angle, in radians.
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0
End Function
```

## <a name="example---log"></a>範例-記錄

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Log%2A> 方法，傳回數位的自然對數。

```vb
Public Function Asinh(value As Double) As Double
    ' Calculate inverse hyperbolic sine, in radians.
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))
End Function
```

## <a name="example---round"></a>範例-Round

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Round%2A> 方法，將數位四捨五入至最接近的整數。

```vb
Dim myVar2 As Double = Math.Round(2.8)
Console.WriteLine(myVar2)
' The code produces the following output:
' 3
```

## <a name="example---sign"></a>範例-Sign

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Sign%2A> 方法來判斷數位的正負號。

```vb
Dim mySign1 As Integer = Math.Sign(12)
Dim mySign2 As Integer = Math.Sign(-2.4)
Dim mySign3 As Integer = Math.Sign(0)
Console.WriteLine(mySign1)
Console.WriteLine(mySign2)
Console.WriteLine(mySign3)
' The code produces the following output:
' 1
' -1
' 0
```

## <a name="example---sin"></a>範例-Sin

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Sin%2A> 方法來傳回角度的正弦值。

```vb
Public Function Csc(angle As Double) As Double
    ' Calculate cosecant of an angle, in radians.
    Return 1.0 / Math.Sin(angle)
End Function
```

## <a name="example---sqrt"></a>範例-Sqrt

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Sqrt%2A> 方法來計算數位的平方根。

```vb
Dim mySqrt1 As Double = Math.Sqrt(4)
Dim mySqrt2 As Double = Math.Sqrt(23)
Dim mySqrt3 As Double = Math.Sqrt(0)
Dim mySqrt4 As Double = Math.Sqrt(-4)
Console.WriteLine(mySqrt1)
Console.WriteLine(mySqrt2)
Console.WriteLine(mySqrt3)
Console.WriteLine(mySqrt4)
' The code produces the following output:
' 2
' 4.79583152331272
' 0
' NaN
```

## <a name="example---tan"></a>範例-Tan

這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Tan%2A> 方法來傳回角度的正切函數。

```vb
Public Function Ctan(angle As Double) As Double
    ' Calculate cotangent of an angle, in radians.
    Return 1.0 / Math.Tan(angle)
End Function
```

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [衍生的數學函式](../keywords/derived-math-functions.md)
- [算術運算子](../operators/arithmetic-operators.md)

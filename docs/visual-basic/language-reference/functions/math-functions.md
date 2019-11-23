---
title: 數學函式
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: b1cd6a846a7dc1dddcf6bdb5eb99ebc1c57a012c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348067"
---
# <a name="math-functions-visual-basic"></a>數學函式 (Visual Basic)
The methods of the <xref:System.Math?displayProperty=nameWithType> class provide trigonometric, logarithmic, and other common mathematical functions.  
  
## <a name="remarks"></a>備註  
 The following table lists methods of the <xref:System.Math?displayProperty=nameWithType> class. You can use these in a Visual Basic program.  
  
|.NET method|描述|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|傳回一個數字的絕對值。|  
|<xref:System.Math.Acos%2A>|傳回餘弦函數 (Cosine) 是指定數字的角。|  
|<xref:System.Math.Asin%2A>|傳回正弦函數 (Sine) 是指定數字的角。|  
|<xref:System.Math.Atan%2A>|傳回正切函數 (Tangent) 是指定數字的角。|  
|<xref:System.Math.Atan2%2A>|傳回正切函數是兩個指定數字之商數的角。|  
|<xref:System.Math.BigMul%2A>|Returns the full product of two 32-bit numbers.|  
|<xref:System.Math.Ceiling%2A>|Returns the smallest integral value that's greater than or equal to the specified `Decimal` or `Double`.|  
|<xref:System.Math.Cos%2A>|傳回指定角的餘弦函數。|  
|<xref:System.Math.Cosh%2A>|傳回指定角的雙曲線餘弦函數。|  
|<xref:System.Math.DivRem%2A>|Returns the quotient of two 32-bit or 64-bit signed integers, and also returns the remainder in an output parameter.|  
|<xref:System.Math.Exp%2A>|Returns e (the base of natural logarithms) raised to the specified power.|  
|<xref:System.Math.Floor%2A>|Returns the largest integer that's less than or equal to the specified `Decimal` or `Double` number.|  
|<xref:System.Math.IEEERemainder%2A>|Returns the remainder that results from the division of a specified number by another specified number.|  
|<xref:System.Math.Log%2A>|Returns the natural (base e) logarithm of a specified number or the logarithm of a specified number in a specified base.|  
|<xref:System.Math.Log10%2A>|傳回指定數字的以 10 為底數的對數。|  
|<xref:System.Math.Max%2A>|Returns the larger of two numbers.|  
|<xref:System.Math.Min%2A>|傳回兩個數字中較小的一個。|  
|<xref:System.Math.Pow%2A>|傳回具有指定乘冪數的指定數字。|  
|<xref:System.Math.Round%2A>|Returns a `Decimal` or `Double` value rounded to the nearest integral value or to a specified number of fractional digits.|  
|<xref:System.Math.Sign%2A>|Returns an `Integer` value indicating the sign of a number.|  
|<xref:System.Math.Sin%2A>|傳回指定角的正弦函數。|  
|<xref:System.Math.Sinh%2A>|傳回指定角的雙曲線正弦函數。|  
|<xref:System.Math.Sqrt%2A>|傳回指定數字的平方根。|  
|<xref:System.Math.Tan%2A>|傳回指定角的正切函數。|  
|<xref:System.Math.Tanh%2A>|傳回指定角的雙曲線正切函數。|  
|<xref:System.Math.Truncate%2A>|Calculates the integral part of a specified `Decimal` or `Double` number.|  
  
 To use these functions without qualification, import the <xref:System.Math?displayProperty=nameWithType> namespace into your project by adding the following code to the top of your source file:  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Abs%2A> method of the <xref:System.Math> class to compute the absolute value of a number.  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Atan%2A> method of the <xref:System.Math> class to calculate the value of pi.  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Cos%2A> method of the <xref:System.Math> class to return the cosine of an angle.  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Exp%2A> method of the <xref:System.Math> class to return e raised to a power.  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Log%2A> method of the <xref:System.Math> class to return the natural logarithm of a number.  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Round%2A> method of the <xref:System.Math> class to round a number to the nearest integer.  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Sign%2A> method of the <xref:System.Math> class to determine the sign of a number.  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Sin%2A> method of the <xref:System.Math> class to return the sine of an angle.  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Sqrt%2A> method of the <xref:System.Math> class to calculate the square root of a number.  
  
```vb
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## <a name="example"></a>範例  
 This example uses the <xref:System.Math.Tan%2A> method of the <xref:System.Math> class to return the tangent of an angle.  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>需求  
 **類別︰** <xref:System.Math>  
  
 **命名空間︰** <xref:System>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [衍生的數學函式](../../../visual-basic/language-reference/keywords/derived-math-functions.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)

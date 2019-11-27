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
<xref:System.Math?displayProperty=nameWithType> 類別的方法會提供三角、對數和其他一般數學函數。  
  
## <a name="remarks"></a>備註  
 下表列出 <xref:System.Math?displayProperty=nameWithType> 類別的方法。 您可以在 Visual Basic 程式中使用這些專案。  
  
|.NET 方法|描述|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|傳回一個數字的絕對值。|  
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
  
 若要在未限定的情況下使用這些函式，請將下列程式碼新增至原始程式檔的頂端，以將 <xref:System.Math?displayProperty=nameWithType> 命名空間匯入至您的專案：  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Abs%2A> 方法來計算數位的絕對值。  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Atan%2A> 方法來計算 pi 的值。  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Cos%2A> 方法來傳回角度的余弦值。  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Exp%2A> 方法，將 e 次方傳回給乘冪。  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Log%2A> 方法，傳回數位的自然對數。  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Round%2A> 方法，將數位四捨五入至最接近的整數。  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Sign%2A> 方法來判斷數位的正負號。  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Sin%2A> 方法來傳回角度的正弦值。  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Sqrt%2A> 方法來計算數位的平方根。  
  
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
 這個範例會使用 <xref:System.Math> 類別的 <xref:System.Math.Tan%2A> 方法來傳回角度的正切函數。  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>需求  
 **類別︰** <xref:System.Math>  
  
 **命名空間︰** <xref:System>  
  
 **元件：** mscorlib （在 mscorlib.dll 中）  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [衍生的數學函式](../../../visual-basic/language-reference/keywords/derived-math-functions.md)
- [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)

---
title: 數學函式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: da0b612feb5b9a479d50f52cf65e38007ab3b196
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746519"
---
# <a name="math-functions-visual-basic"></a>數學函式 (Visual Basic)
方法的<xref:System.Math?displayProperty=nameWithType>類別提供三角函數、 對數以及其他一般數學函數。  
  
## <a name="remarks"></a>備註  
 下表列出的方法<xref:System.Math?displayProperty=nameWithType>類別。 您可以使用這些功能的 Visual Basic 程式。  
  
|.NET 方法|描述|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|傳回一個數字的絕對值。|  
|<xref:System.Math.Acos%2A>|傳回餘弦函數 (Cosine) 是指定數字的角。|  
|<xref:System.Math.Asin%2A>|傳回正弦函數 (Sine) 是指定數字的角。|  
|<xref:System.Math.Atan%2A>|傳回正切函數 (Tangent) 是指定數字的角。|  
|<xref:System.Math.Atan2%2A>|傳回正切函數是兩個指定數字之商數的角。|  
|<xref:System.Math.BigMul%2A>|傳回兩個 32 位元數字的完整的產品。|  
|<xref:System.Math.Ceiling%2A>|傳回大於或等於指定的最小整數值`Decimal`或`Double`。|  
|<xref:System.Math.Cos%2A>|傳回指定角的餘弦函數。|  
|<xref:System.Math.Cosh%2A>|傳回指定角的雙曲線餘弦函數。|  
|<xref:System.Math.DivRem%2A>|傳回兩個 32 位元或 64 位元帶正負號的整數，商數，並傳回餘數做為輸出參數。|  
|<xref:System.Math.Exp%2A>|傳回指定次方的 e （自然對數的基底）。|  
|<xref:System.Math.Floor%2A>|傳回小於或等於指定的最大整數`Decimal`或`Double`數目。|  
|<xref:System.Math.IEEERemainder%2A>|傳回指定數目的所得另一個指定數字相除的餘數。|  
|<xref:System.Math.Log%2A>|在指定的基底會傳回指定數字的自然 （底數為 e） 對數或指定的數字的對數。|  
|<xref:System.Math.Log10%2A>|傳回指定數字的以 10 為底數的對數。|  
|<xref:System.Math.Max%2A>|傳回兩個數字的較大。|  
|<xref:System.Math.Min%2A>|傳回兩個數字中較小的一個。|  
|<xref:System.Math.Pow%2A>|傳回具有指定乘冪數的指定數字。|  
|<xref:System.Math.Round%2A>|傳回`Decimal`或`Double`值四捨五入為最接近的整數值，或指定的小數位數。|  
|<xref:System.Math.Sign%2A>|傳回`Integer`指示數字的正負號的值。|  
|<xref:System.Math.Sin%2A>|傳回指定角的正弦函數。|  
|<xref:System.Math.Sinh%2A>|傳回指定角的雙曲線正弦函數。|  
|<xref:System.Math.Sqrt%2A>|傳回指定數字的平方根。|  
|<xref:System.Math.Tan%2A>|傳回指定角的正切函數。|  
|<xref:System.Math.Tanh%2A>|傳回指定角的雙曲線正切函數。|  
|<xref:System.Math.Truncate%2A>|計算指定的整數部分`Decimal`或`Double`數目。|  
  
 若要使用這些函式，但是不限定，匯入<xref:System.Math?displayProperty=nameWithType>到您的專案加入原始程式檔頂端新增下列程式碼的命名空間：  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Abs%2A>方法的<xref:System.Math>類別來計算數字的絕對值。  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Atan%2A>方法的<xref:System.Math>類別來計算 pi 的值。  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Cos%2A>方法的<xref:System.Math>類別，以傳回某個角度的餘弦值。  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Exp%2A>方法的<xref:System.Math>類別，以傳回 e 的乘冪。  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Log%2A>方法的<xref:System.Math>類別，以傳回數字的自然對數。  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Round%2A>方法的<xref:System.Math>類別來將數值四捨五入到最接近的整數。  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Sign%2A>方法的<xref:System.Math>類別，以判斷數字的正負號。  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Sin%2A>方法的<xref:System.Math>類別，以傳回某個角度的正弦值。  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Math.Sqrt%2A>方法的<xref:System.Math>類別以計算數字的平方根。  
  
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
 這個範例會使用<xref:System.Math.Tan%2A>方法的<xref:System.Math>類別，以傳回某個角度的正切。  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>需求  
 **類別：** <xref:System.Math>  
  
 **命名空間：** <xref:System>  
  
 **組件：** mscorlib （在 mscorlib.dll 中)  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>  
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>  
 <xref:System.Double.NaN>  
 [衍生的數學函式](../../../visual-basic/language-reference/keywords/derived-math-functions.md)  
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)

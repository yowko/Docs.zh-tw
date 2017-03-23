---
title: "數學函式 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "數學函式，Visual Basic"
  - "數學運算，數學函式"
  - "數學常式"
  - "Atn 函式"
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# 數學函式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

<xref:System.Math?displayProperty=fullName> 類別中的方法提供三角，對數函數和其他一般數學函式。  
  
## 備註  
 下表列出 <xref:System.Math?displayProperty=fullName> 類別中的方法。  您可以使用 Visual Basic 程式中使用這些。  
  
|.NET Framework 方法|描述|  
|-----------------------|--------|  
|<xref:System.Math.Abs%2A>|傳回數值的絕對值。|  
|<xref:System.Math.Acos%2A>|傳回餘弦函數 \(Cosine\) 是指定數字的角。|  
|<xref:System.Math.Asin%2A>|傳回正弦函數 \(Sine\) 是指定數字的角。|  
|<xref:System.Math.Atan%2A>|傳回正切函數 \(Tangent\) 是指定數字的角。|  
|<xref:System.Math.Atan2%2A>|傳回正切函數是兩個指定數字之商數的角。|  
|<xref:System.Math.BigMul%2A>|傳回兩個 32 位元數字完整的產品。|  
|<xref:System.Math.Ceiling%2A>|傳回大於或等於指定之 `Decimal` 或 `Double`的最小整數值。|  
|<xref:System.Math.Cos%2A>|傳回指定角的餘弦函數。|  
|<xref:System.Math.Cosh%2A>|傳回指定角的雙曲線餘弦函數。|  
|<xref:System.Math.DivRem%2A>|傳回兩個 32 位元或 64 位元帶正負號的整數商數，也會在輸出參數。|  
|<xref:System.Math.Exp%2A>|傳回 e \(自然對數的基數\) 的乘至指定的乘冪數。|  
|<xref:System.Math.Floor%2A>|傳回小於或等於指定之 `Decimal` 或 `Double` 數字的最大整數。|  
|<xref:System.Math.IEEERemainder%2A>|傳回指定數字的除法運算的結果為另一個指定數字的其餘部分。|  
|<xref:System.Math.Log%2A>|傳回指定數字的自然 \(底數為 e\) 對數或指定數字的對數在指定的基底。|  
|<xref:System.Math.Log10%2A>|傳回指定數字的底數 10 對數。|  
|<xref:System.Math.Max%2A>|傳回兩個大數字。|  
|<xref:System.Math.Min%2A>|傳回兩個數字中較小的一個。|  
|<xref:System.Math.Pow%2A>|傳回具有指定乘冪數的指定數字。|  
|<xref:System.Math.Round%2A>|傳回 `Decimal` 或 `Double` 值會捨入為最接近的整數值或為小數位數的指定數目。|  
|<xref:System.Math.Sign%2A>|傳回表示數字正負號的 `Integer` 值。|  
|<xref:System.Math.Sin%2A>|傳回指定角的正弦函數。|  
|<xref:System.Math.Sinh%2A>|傳回指定角的雙曲線正弦函數。|  
|<xref:System.Math.Sqrt%2A>|傳回指定數字的平方根。|  
|<xref:System.Math.Tan%2A>|傳回指定角的正切函數。|  
|<xref:System.Math.Tanh%2A>|傳回指定角的雙曲線正切函數。|  
|<xref:System.Math.Truncate%2A>|計算指定的 `Decimal` 或 `Double` 數字的整數部分。|  
  
 若要使用這些函式，不需完整，請匯入 <xref:System.Math?displayProperty=fullName> 命名空間匯入您的專案將下列程式碼加入至原始程式檔的最前面:  
  
```  
Imports System.Math  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Abs%2A> 方法來計算數字的絕對值。  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Atan%2A> 方法來計算 pi 的值。  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Cos%2A> 方法來傳回角度的餘弦函數 \(Cosine\)。  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Exp%2A> 方法傳回乘冪數的 e。  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Log%2A> 方法來傳回數字的自然對數。  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Round%2A> 方法來將數字捨入為最接近的整數。  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Sign%2A> 方法來決定數字的正負號。  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Sin%2A> 方法來傳回角度的正弦函數 \(Sine\)。  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Sqrt%2A> 方法來計算數字的平方根。  
  
```  
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## 範例  
 這個範例使用 <xref:System.Math> 類別的 <xref:System.Math.Tan%2A> 方法來傳回角度的正切函數 \(Tangent\)。  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## 需求  
 **類別︰** <xref:System.Math>  
  
 **命名空間︰** <xref:System>  
  
 **組件：**mscorlib \(在 mscorlib.dll 中\)  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>   
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>   
 <xref:System.Double.NaN>   
 [Derived Math Functions](../../../visual-basic/language-reference/keywords/derived-math-functions.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
---
title: "如何：以前置字元零來填補數字"
description: "如何以前置字元零來填補數字"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a517c066-b11e-4815-826b-9262611eac40
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 0a136d88dfbc83d40ff8a204f275537c24f9748b

---

# <a name="how-to-pad-a-number-with-leading-zeros"></a>如何：以前置字元零來填補數字

如果整數要加上前置零，您可以使用具有精確度規範的 "D" [標準數值格式字串](standard-numeric.md)。 如果整數和浮點數都要加上前置零，您可以使用[自訂數值格式字串](custom-numeric.md)。 此主題示範如何使用這兩種方法，以前置零填補數值。

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>以前置零將整數填補至特定長度

1. 決定您要整數值顯示的位數下限。 在此數值中包含任何前置數。

2. 決定要將整數顯示為十進位值或十六進位值。

    * 若要將整數顯示為十進位值，請呼叫其 `ToString(String)` 方法，然後傳遞字串 "D*n*" 以作為 format 參數的值，其中 *n* 代表字串的長度下限。
    
    * 若要將整數顯示為十進位值，請呼叫其 `ToString(String)` 方法，然後傳遞字串 "X*n*" 以作為 format 參數的值，其中 *n* 代表字串的長度下限。
    
  您也可以在使用[複合格式](composite-format.md)的方法 (例如 [Console.WriteLine](xref:System.Console.WriteLine) 或 [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))) 中使用格式字串。  
  
下列範例會使用前置零來將數個整數值格式化，讓格式化數值的總長度至少為 8 個字元。

```csharp
byte byteValue = 254;
short shortValue = 10342;
int intValue = 1023983;
long lngValue = 6985321;               
ulong ulngValue = UInt64.MaxValue;

// Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"));
Console.WriteLine();

// Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue);
// The example displays the following output:
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//       
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//         18446744073709551615       FFFFFFFFFFFFFFFF
```

```vb
Dim byteValue As Byte = 254
Dim shortValue As Short = 10342
Dim intValue As Integer = 1023983
Dim lngValue As Long = 6985321               
Dim ulngValue As ULong = UInt64.MaxValue

' Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"))
Console.WriteLine()

' Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue)
' The example displays the following output:
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
'       
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
```

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>以特定數目的前置零填補整數

1. 決定您想要讓整數值顯示多少個前置零。

2. 決定要將整數顯示為十進位值或十六進位值。 若要將其格式化為十進位值，您需要使用 "D" 標準格式規範；若要將其格式化為十六進位值，您需要使用 "X" 標準格式規範。

3. 呼叫整數值的 `ToString("D").Length` 或 `ToString("X").Length` 方法，以決定未填補之數值字串的長度。 

4. 將您想要包含在格式化字串中的前置零個數，加入至未填補之數值字串的長度。 這會定義填補字串的總長度。

5. 呼叫整數值的 `ToString(String)` 方法，針對十進位字串，請傳遞字串 "D*n*"，針對十六進位字串，請傳遞 "X*n*"，其中 *n* 代表填補字串的總長度。 您也可以在支援複合格式的方法中，使用 "D*n*" 或 "X*n*" 格式字串。

下列範例會以五個前置零填補整數值。

```csharp
int value = 160934;
int decimalLength = value.ToString("D").Length + 5;
int hexLength = value.ToString("X").Length + 5;
Console.WriteLine(value.ToString("D" + decimalLength.ToString()));
Console.WriteLine(value.ToString("X" + hexLength.ToString()));
// The example displays the following output:
//       00000160934
//       00000274A6
```

```vb
Dim value As Integer = 160934
Dim decimalLength As Integer = value.ToString("D").Length + 5
Dim hexLength As Integer = value.ToString("X").Length + 5
Console.WriteLine(value.ToString("D" + decimalLength.ToString()))
Console.WriteLine(value.ToString("X" + hexLength.ToString()))
' The example displays the following output:
'       00000160934
'       00000274A6 
```

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>以前置零將數值填補至特定長度

1. 決定您想要讓數值字串表示式的小數點左邊有幾位數。 在這個總位數中包含任何前置零。

2. 定義自訂數值格式字串，使用零預留位置 ("0") 來表示零的數目下限。

3. 呼叫數值的 `ToString(String)` 方法，並將其傳遞至自訂格式字串。 您也可以將自訂格式字串與支援複合格式的方法搭配使用。

下列範例會使用前置零來將數個數值格式化，讓格式化數值的小數點左邊至少有 8 位數。

```csharp
string fmt = "00000000.##";
int intValue = 1053240;
decimal decValue = 103932.52m;
float sngValue = 1549230.10873992f;
double dblValue = 9034521202.93217412;

// Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt));
Console.WriteLine(decValue.ToString(fmt));           
Console.WriteLine(sngValue.ToString(fmt));
Console.WriteLine(dblValue.ToString(fmt));           
Console.WriteLine();

// Display the numbers using composite formatting.
string formatString = " {0,15:" + fmt + "}";
Console.WriteLine(formatString, intValue);      
Console.WriteLine(formatString, decValue);      
Console.WriteLine(formatString, sngValue);      
Console.WriteLine(formatString, dblValue);      
// The example displays the following output:
//       01053240
//       00103932.52
//       01549230
//       9034521202.93
//       
//               01053240
//            00103932.52
//               01549230
//          9034521202.93  
```

```vb
Dim fmt As String = "00000000.##"
Dim intValue As Integer = 1053240
Dim decValue As Decimal = 103932.52d
Dim sngValue As Single = 1549230.10873992
Dim dblValue As Double = 9034521202.93217412

' Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt))
Console.WriteLine(decValue.ToString(fmt))            
Console.WriteLine(sngValue.ToString(fmt))
Console.WriteLine(dblValue.ToString(fmt))            
Console.WriteLine()

' Display the numbers using composite formatting.
Dim formatString As String = " {0,15:" + fmt + "}"
Console.WriteLine(formatString, intValue)      
Console.WriteLine(formatString, decValue)      
Console.WriteLine(formatString, sngValue)      
Console.WriteLine(formatString, dblValue)      
' The example displays the following output:
'       01053240
'       00103932.52
'       01549230
'       9034521202.93
'       
'               01053240
'            00103932.52
'               01549230
'          9034521202.93
```

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>以特定數目的前置零填補數值

1. 決定您想要讓數值有多少個前置零。

2. 決定未填補之數值字串的小數點左邊有幾位數。 做法：

    a. 決定數值字串表示法是否包含小數點符號。
    
    b. 如果包含小數點符號，則要決定小數點左邊的字元數。       
    
    -或-
       
    如果不包含小數點符號，則要決定字串長度。 
       
3. 建立自訂格式字串，使用零預留位置 ("0")，讓每個前置零出現在字串中，並使用零預留位置或數字預留位置 ("#") 來代表預設字串中的每個數字。 

4. 提供自訂格式字串，以作為數值的 ToString(String) 方法或支援複合格式方法的參數。

下列範例會以五個前置零填補兩個 [Double](xref:System.Double) 值。

```csharp
double[] dblValues = { 9034521202.93217412, 9034521202 };
foreach (double dblValue in dblValues)
{
   string decSeparator = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator;
   string fmt, formatString;

   if (dblValue.ToString().Contains(decSeparator))
   {
      int digits = dblValue.ToString().IndexOf(decSeparator);
      fmt = new String('0', 5) + new String('#', digits) + ".##";
   }
   else
   {
      fmt = new String('0', dblValue.ToString().Length);   
   }
   formatString = "{0,20:" + fmt + "}";

   Console.WriteLine(dblValue.ToString(fmt));
   Console.WriteLine(formatString, dblValue);
}
// The example displays the following output:
//       000009034521202.93
//         000009034521202.93
//       9034521202
//                 9034521202 
```

```vb
Dim dblValues() As Double = { 9034521202.93217412, 9034521202 }
For Each dblValue As Double In dblValues
   Dim decSeparator As String = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator
   Dim fmt, formatString As String

   If dblValue.ToString.Contains(decSeparator) Then
      Dim digits As Integer = dblValue.ToString().IndexOf(decSeparator)
      fmt = New String("0"c, 5) + New String("#"c, digits) + ".##"
   Else
      fmt = New String("0"c, dblValue.ToString.Length)   
   End If
   formatString = "{0,20:" + fmt + "}"

   Console.WriteLine(dblValue.ToString(fmt))
   Console.WriteLine(formatString, dblValue)
Next
' The example displays the following output:
'       000009034521202.93
'         000009034521202.93
'       9034521202
'                 9034521202
```

## <a name="see-also"></a>另請參閱

[標準數值格式字串](standard-numeric.md)

[自訂數值格式字串](custom-numeric.md)

[複合格式](composite-format.md)




<!--HONumber=Nov16_HO3-->



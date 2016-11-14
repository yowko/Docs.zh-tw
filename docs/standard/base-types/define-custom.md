---
title: "如何：定義和使用自訂數值格式提供者"
description: "如何定義和使用自訂數值格式提供者"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9b184114-6612-4c1a-a2db-2e24e65b0f77
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 926195e48e9653525a502cf9403ae9c205bd0fe3

---

# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>如何：定義和使用自訂數值格式提供者

.NET 可讓您有效掌控數值的字串表示。 它支援以下自訂數值格式的功能：

* 標準數值格式字串，這些字串提供預先定義的格式集，可將數字轉換成其字串表示。 您可以使用這些字串搭配任何擁有 format 參數的數值格式化方法，例如 [Decimal.ToString(String](xref:System.Decimal.ToString(System.String))。 如需詳細資訊，請參閱[標準數值格式字串](standard-numeric.md)。

* 自訂數值格式字串，這些字串提供能夠合併的符號集，可用來定義自訂數值格式規範。 些字串可以搭配任何擁有 format 參數的數值格式化方法使用，例如 [Decimal.ToString(String](xref:System.Decimal.ToString(System.String))。 如需詳細資訊，請參閱[自訂數值格式字串](custom-numeric.md)。

* 自訂 [CultureInfo](xref:System.Globalization.CultureInfo) 或 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，該物件定義用來顯示數值之字串表示的符號和格式模式。 您可以使用這些字串搭配任何擁有 *provider* 參數的數值格式化方法，例如 [ToString](xref:System.Int32.ToString(System.IFormatProvider))。 一般而言，*provider* 參數會用來指定文化特性專屬的格式。

在某些情況下，這三項技術並不適用 (例如，應用程式必須顯示格式化帳號、身分證號碼或是郵遞區號時)。 .NET 還可讓您定義決定如何格式化數值的格式物件，該物件既不是 [CultureInfo](xref:System.Globalization.CultureInfo) 也不是 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件。 本主題提供實作這類物件的逐步指示，並提供格式化電話號碼的範例。

## <a name="to-define-a-custom-format-provider"></a>定義自訂格式提供者

1. 定義實作 [IFormatProvider](xref:System.IFormatProvider) 和 [ICustomFormatter](xref:System.ICustomFormatter) 介面的類別。 

2. 實作 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 方法。 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 是格式化方法 (例如 [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法) 叫用的回呼方法，用來擷取實際負責執行自訂格式的物件。 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 的一般實作會執行下列操作：

    a. 判斷作為方法參數傳遞的 [Type](xref:System.Type) 物件是否代表 [ICustomFormatter](xref:System.ICustomFormatter) 介面。
    
    b. 如果參數確實代表 [ICustomFormatter](xref:System.ICustomFormatter) 介面，則 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 會傳回實作 [ICustomFormatter](xref:System.ICustomFormatter) 介面的物件，該介面負責提供自訂格式。 一般而言，自訂格式物件會自行傳回。 
    
    c.  如果參數不代表 [ICustomFormatter](xref:System.ICustomFormatter) 介面，則 [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 會傳回 `null`。
    
3. 實作 [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法。 這個方法是由 [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法呼叫，並且負責傳回數字的字串表示。 實作這個方法通常包含下列各項：

    a. (選擇性) 檢查 *provider* 參數，確認這個方法的合法目的為提供格式化服務。 針對實作 [IFormatProvider](xref:System.IFormatProvider) 與 [ICustomFormatter](xref:System.ICustomFormatter) 的格式物件，這項檢查包含測試 *provider* 參數是否與目前的格式物件相等。
    
    b. 決定格式物件是否應支援自訂格式規範 (例如，"N" 格式規範可能表示應使用 NANP 格式輸出美國電話號碼，而 "I" 可能表示使用 ITU-T Recommendation E.123 格式輸出)。如果使用格式規範，則這個方法應處理特定格式規範。 格式規範會隨 format 參數傳遞至方法。 如果沒有規範，則 *format* 參數值為 [String.Empty](xref:System.String#System_String_Empty)。
    
    c.  擷取作為 *arg* 參數傳遞至方法的數值。 執行任何必要的操作，將它轉換成其字串表示。
    
    d. 傳回 *arg* 參數的字串表示。
    
## <a name="to-use-a-custom-numeric-formatting-object"></a>使用自訂數值格式物件

1. 建立自訂格式類別的新執行個體。

2. 呼叫 [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 格式化方法，將自訂格式物件、格式規範 (沒有使用的話則為 [String.Empty](xref:System.String.Empty)) 及要格式化的數值傳遞給該方法。 

## <a name="example"></a>範例

下列範例會定義名為 `TelephoneFormatter` 的自訂數值格式提供者，它會將代表美國電話號碼的數字轉換成 NANP 或 E.123 格式。 這個方法會處理兩種格式規範："N" (輸出 NANP 格式) 和 "I" (輸出國際 E.123 格式)。

```csharp
using System;
using System.Globalization;

public class TelephoneFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   {
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }               

   public string Format(string format, object arg, IFormatProvider formatProvider)
   {
      // Check whether this is an appropriate callback             
      if (! this.Equals(formatProvider))
         return null; 

      // Set default format specifier             
      if (string.IsNullOrEmpty(format)) 
         format = "N";

      string numericString = arg.ToString();

      if (format == "N")
      {
         if (numericString.Length <= 4)
            return numericString;
         else if (numericString.Length == 7)
            return numericString.Substring(0, 3) + "-" + numericString.Substring(3, 4); 
         else if (numericString.Length == 10)
               return "(" + numericString.Substring(0, 3) + ") " +
                      numericString.Substring(3, 3) + "-" + numericString.Substring(6);   
         else
            throw new FormatException( 
                      string.Format("'{0}' cannot be used to format {1}.", 
                                    format, arg.ToString()));
      }
      else if (format == "I")
      {
         if (numericString.Length < 10)
            throw new FormatException(string.Format("{0} does not have 10 digits.", arg.ToString()));
         else
            numericString = "+1 " + numericString.Substring(0, 3) + " " + numericString.Substring(3, 3) + " " + numericString.Substring(6);
      }
      else
      {
         throw new FormatException(string.Format("The {0} format specifier is invalid.", format));
      } 
      return numericString;  
   }
}

public class TestTelephoneFormatter
{
   public static void Main()
   {
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:I}", 4257884748));
   }
}
```

```vb
Public Class TelephoneFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If               
   End Function               

   Public Function Format(fmt As String, arg As Object, _
                          formatProvider As IFormatProvider) As String _
                   Implements ICustomFormatter.Format
      ' Check whether this is an appropriate callback             
      If Not Me.Equals(formatProvider) Then Return Nothing 

      ' Set default format specifier             
      If String.IsNullOrEmpty(fmt) Then fmt = "N"

      Dim numericString As String = arg.ToString

      If fmt = "N" Then
         Select Case numericString.Length
            Case <= 4 
               Return numericString
            Case 7
               Return Left(numericString, 3) & "-" & Mid(numericString, 4) 
            Case 10
               Return "(" & Left(numericString, 3) & ") " & _
                      Mid(numericString, 4, 3) & "-" & Mid(numericString, 7)   
            Case Else
               Throw New FormatException( _
                         String.Format("'{0}' cannot be used to format {1}.", _
                                       fmt, arg.ToString()))
         End Select
      ElseIf fmt = "I" Then
         If numericString.Length < 10 Then
            Throw New FormatException(String.Format("{0} does not have 10 digits.", arg.ToString()))
         Else
            numericString = "+1 " & Left(numericString, 3) & " " & Mid(numericString, 4, 3) & " " & Mid(numericString, 7)
         End If      
      Else
         Throw New FormatException(String.Format("The {0} format specifier is invalid.", fmt))
      End If 
      Return numericString  
   End Function
End Class

Public Module TestTelephoneFormatter
   Public Sub Main
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:I}", 4257884748))
   End Sub
End Module
```

自訂數值格式提供者只能搭配 [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法使用。 其他擁有 [IFormatProvider](xref:System.IFormatProvider) 型別參數的數值格式化方法多載 (例如 `ToString`)，全都會將代表 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 型別的 [Type](xref:System.Type) 物件傳遞給 [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) 實作。 接著這些多載會預期方法傳回 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件。 如果方法未傳回該物件，則會忽略自訂數值格式提供者，並且使用目前文化特性的 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件取代。 在此範例中，`TelephoneFormatter.GetFormat` 方法會檢查方法參數及傳回 *null* (如果其代表 [ICustomFormatter](xref:System.ICustomFormatter) 以外的型別)，藉此處理可能不當傳遞至數值格式化方法的情況。

自訂數值格式提供者支援格式規範集時，如果 [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法呼叫中使用的格式項目未提供格式規範，則務必確實提供預設的行為。 在此範例中，"N" 是預設的格式規範。 如此即可提供明確格式規範，將數字轉換成格式化的電話號碼。 下列範例說明這類方法呼叫。

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))
```

不過，它也允許在沒有格式規範的情況下進行轉換。 下列範例說明這類方法呼叫。

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))
```

如果未定義預設的格式規範，您的 [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 方法實作就應包含下面所示的程式碼，如此 .NET Framework 才能提供您的程式碼不支援的格式。

```csharp
if (arg is IFormattable) 
   s = ((IFormattable)arg).ToString(format, formatProvider);
else if (arg != null)    
   s = arg.ToString();
```

```vb
If TypeOf(arg) Is IFormattable Then 
   s = DirectCast(arg, IFormattable).ToString(fmt, formatProvider)
ElseIf arg IsNot Nothing Then    
   s = arg.ToString()
End If
```

在此範例中，實作 [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) 的方法將作為 [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) 方法的回呼方法。 因此，它會檢查 *formatProvider* 參數，以判斷其中是否包含目前 `TelephoneFormatter` 物件的參考。 不過，此方法也可以直接從程式碼呼叫。 在此情況下，您可以使用 *formatProvider *參數提供 [CultureInfo](xref:System.Globalization.CultureInfo) 或 [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) 物件，該物件會提供文化特性專屬的格式資訊。

## <a name="see-also"></a>另請參閱

[執行格式化作業](performing-formatting-operations.md)



<!--HONumber=Nov16_HO1-->



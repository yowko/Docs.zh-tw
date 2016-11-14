---
title: "使用 StringBuilder 類別"
description: "使用 StringBuilder 類別"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f4f5d1c7-d84d-4867-810f-2708cd6de0da
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 1e8453b78827d8c02f29135ddfb832956ab40f3c

---

# <a name="using-the-stringbuilder-class"></a>使用 StringBuilder 類別

[String](xref:System.String) 物件為不可變。 每當您使用 [System.String](xref:System.String) 類別的其中一個方法時，您會在記憶體中建立新的字串物件，而系統即需為這個新物件配置新的空間。 在您需要重複修改字串的情況下，建立新 [String](xref:System.String) 物件時產生的額外負荷可能成本高昂。 [System.Text.StringBuilder](xref:System.Text.StringBuilder) 類別可用於您想要修改字串，而不建立新的物件時。 例如，使用 [StringBuilder](xref:System.Text.StringBuilder) 類別可以在將許多字串一起串連在迴圈中時，提升效能。

## <a name="importing-the-systemtext-namespace"></a>匯入 System.Text 命名空間

[StringBuilder](xref:System.Text.StringBuilder) 類別位於 [System.Text](xref:System.Text) 命名空間。 若要避免在程式碼中提供完整的類型名稱，您可以匯入 [System.Text](xref:System.Text) 命名空間： 

```csharp
using System;
using System.Text;
```

```vb
Imports System.Text
```

## <a name="instantiating-a-stringbuilder-object"></a>具現化 StringBuilder 物件

您可以使用其中一個多載建構函式方法，初始化變數來建立 [StringBuilder](xref:System.Text.StringBuilder) 類別的新執行個體，如下列範例所示。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
```

## <a name="setting-the-capacity-and-length"></a>設定容量和長度

雖然 [StringBuilder](xref:System.Text.StringBuilder) 是動態的物件 (可讓您擴展它所封裝之字串中的字元數)，但您仍可以指定它能容納的字元數上限值。 這個值稱為物件的容量，不應該與目前 [StringBuilder](xref:System.Text.StringBuilder) 保存的字串長度混淆。 例如，您可以用字串 "Hello" 建立 [StringBuilder](xref:System.Text.StringBuilder) 類別的新執行個體，其長度為 5，而且您可能會指定物件的最大容量為 25。 當您修改 [StringBuilder](xref:System.Text.StringBuilder) 時，除非達到容量上限，否則它不會重新配置自己的大小。 發生這種情況時，會自動配置新的空間，而且容量加倍。 您可以使用其中一個多載建構函式，指定 [StringBuilder](xref:System.Text.StringBuilder) 類別的容量。 下列範例會指定 `MyStringBuilder` 物件可以擴展到最多 25 個空格。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!", 25);
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!", 25) 
```

此外，您可以使用讀/寫 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性來設定物件的長度上限。 下列範例會使用 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性來定義物件長度上限。

```csharp
MyStringBuilder.Capacity = 25;
```

```vb
MyStringBuilder.Capacity = 25
```

[EnsureCapacity](xref:System.Text.StringBuilder.EnsureCapacity(System.Int32)) 方法可用來檢查目前 [StringBuilder](xref:System.Text.StringBuilder) 的容量。 如果容量大於傳遞的值，不會進行任何變更。不過，如果容量小於傳遞的值，會變更目前的容量以符合傳遞的值。

您也可以檢視或設定 [Length](xref:System.Text.StringBuilder.Length) 屬性。 如果您將 [Length](xref:System.Text.StringBuilder.Length) 屬性的值設成大於 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性的值，則 [Capacity](xref:System.Text.StringBuilder.Capacity) 屬性會自動變更為與 [Length](xref:System.Text.StringBuilder.Length) 屬性相同的值。 若將 [Length](xref:System.Text.StringBuilder.Length) 屬性的值設成小於目前 [StringBuilder](xref:System.Text.StringBuilder) 內字串長度的值，則會縮短該字串。

## <a name="modifying-the-stringbuilder-string"></a>修改 StringBuilder 字串

下表列出您可用來修改 [StringBuilder](xref:System.Text.StringBuilder) 內容的方法。

方法名稱 | 用法
----------- | ---
[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) | 將資訊附加至目前 [StringBuilder](xref:System.Text.StringBuilder) 的結尾。
[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) | 將字串中傳遞的格式規範取代為格式化的文字。
[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) | 將字串或物件插入目前 [StringBuilder](xref:System.Text.StringBuilder) 的指定索引。
[StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) | 從目前 [StringBuilder](xref:System.Text.StringBuilder) 移除指定的字元數。
[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 取代指定索引處的指定字元。

### <a name="append"></a>附加

[StringBuilder.Append](xref:System.Text.StringBuilder.Append(System.Char)) 方法可以用來將物件的文字或字串表示新增至目前 [StringBuilder](xref:System.Text.StringBuilder) 所代表的字串結尾。 下列範例會將 [StringBuilder](xref:System.Text.StringBuilder) 初始化為 "Hello World"，然後附加一些文字到物件的結尾。 會視需要自動配置空格。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Append(" What a beautiful day.");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World! What a beautiful day.
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Append(" What a beautiful day.")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World! What a beautiful day.
```

### <a name="appendformat"></a>AppendFormat

[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) 方法會將文字新增至 [StringBuilder](xref:System.Text.StringBuilder) 物件的結尾。 它支援複合格式設定功能 (如需詳細資訊，請參閱[複合格式設定](composite-format.md))，方法是呼叫要格式化之物件的 [IFormattable](xref:System.IFormattable) 實作。 因此，它接受數值、日期和時間，以及列舉值的標準格式字串，數值及日期和時間的自訂格式字串，以及為自訂類型定義的格式字串。 (如需格式設定的資訊，請參閱[格式化類型](formatting-types.md)。)您可以使用這個方法，自訂變數的格式，並將那些值附加到 [StringBuilder](xref:System.Text.StringBuilder)。 下列範例會使用 AppendFormat 方法，將格式化為貨幣值的整數值，放到 [StringBuilder](xref:System.Text.StringBuilder) 物件的結尾。

```csharp
int MyInt = 25; 
StringBuilder MyStringBuilder = new StringBuilder("Your total is ");
MyStringBuilder.AppendFormat("{0:C} ", MyInt);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Your total is $25.00
```

```vb
Dim MyInt As Integer = 25
Dim MyStringBuilder As New StringBuilder("Your total is ")
MyStringBuilder.AppendFormat("{0:C} ", MyInt)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'     Your total is $25.00 
```

### <a name="insert"></a>Insert

[StringBuilder.Insert](xref:System.Text.StringBuilder.Insert(System.Int32,System.Char)) 方法會將字串或物件新增至目前 [StringBuilder](xref:System.Text.StringBuilder) 物件中的指定位置。 下列範例會使用這個方法，在 [StringBuilder](xref:System.Text.StringBuilder) 物件的第六個位置插入一個字。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Insert(6,"Beautiful ");
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello Beautiful World!
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Insert(6, "Beautiful ")
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'      Hello Beautiful World!
```

### <a name="remove"></a>移除

您可以使用 [StringBuilder.Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) 方法，從目前 [StringBuilder](xref:System.Text.StringBuilder) 物件移除指定的字元數 (從指定的以零為起始的索引處開始移除)。 下列範例會使用 [Remove](xref:System.Text.StringBuilder.Remove(System.Int32,System.Int32)) 方法來縮短 [StringBuilder](xref:System.Text.StringBuilder) 物件。

```csharp
StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Remove(5,7);
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Remove(5, 7)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello
```

### <a name="replace"></a>取代

[StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 取代指定索引處的指定字元。
方法可以用來將 [StringBuilder](xref:System.Text.StringBuilder) 物件內的字元取代為另一個指定的字元。 下列範例使用 [StringBuilder.Replace](xref:System.Text.StringBuilder.Replace(System.Char,System.Char)) | 取代指定索引處的指定字元。
方法來搜尋 [StringBuilder](xref:System.Text.StringBuilder) 物件中所有的驚嘆號字元 (!) 執行個體，並取代為問號字元 (?)。
 
 ```csharp
 StringBuilder MyStringBuilder = new StringBuilder("Hello World!");
MyStringBuilder.Replace('!', '?');
Console.WriteLine(MyStringBuilder);
// The example displays the following output:
//       Hello World?
```

```vb
Dim MyStringBuilder As New StringBuilder("Hello World!")
MyStringBuilder.Replace("!"c, "?"c)
Console.WriteLine(MyStringBuilder)
' The example displays the following output:
'       Hello World?
```

## <a name="converting-a-stringbuilder-object-to-a-string"></a>將 StringBuilder 物件轉換為字串

您必須先將 [StringBuilder](xref:System.Text.StringBuilder) 物件轉換成 [String](xref:System.String) 物件，才能將 [StringBuilder](xref:System.Text.StringBuilder) 物件所代表的字串傳遞給具有 [String](xref:System.String) 參數的方法，或將它顯示在使用者介面。 您可以藉由呼叫 [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) 方法執行這項轉換。 下列範例會呼叫許多 [StringBuilder](xref:System.Text.StringBuilder) 方法，然後呼叫 [StringBuilder.ToString](xref:System.Text.StringBuilder.ToString) 方法來顯示字串。

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      StringBuilder sb = new StringBuilder();
      bool flag = true;
      string[] spellings = { "recieve", "receeve", "receive" };
      sb.AppendFormat("Which of the following spellings is {0}:", flag);
      sb.AppendLine();
      for (int ctr = 0; ctr <= spellings.GetUpperBound(0); ctr++) {
         sb.AppendFormat("   {0}. {1}", ctr, spellings[ctr]);
         sb.AppendLine();
      }
      sb.AppendLine();
      Console.WriteLine(sb.ToString());
   }
}
// The example displays the following output:
//       Which of the following spellings is True:
//          0. recieve
//          1. receeve
//          2. receive
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim sb As New StringBuilder()
      Dim flag As Boolean = True
      Dim spellings() As String = { "recieve", "receeve", "receive" }
      sb.AppendFormat("Which of the following spellings is {0}:", flag)
      sb.AppendLine()
      For ctr As Integer = 0 To spellings.GetUpperBound(0)
         sb.AppendFormat("   {0}. {1}", ctr, spellings(ctr))
         sb.AppendLine()
      Next
      sb.AppendLine()
      Console.WriteLine(sb.ToString())
   End Sub
End Module
' The example displays the following output:
'       Which of the following spellings is True:
'          0. recieve
'          1. receeve
'          2. receive
```

## <a name="see-also"></a>另請參閱

[System.Text.StringBuilder](xref:System.Text.StringBuilder)

[基本字串作業](basic-string-operations.md)

[格式化類型](formatting-types.md)



<!--HONumber=Nov16_HO1-->



---
title: "比較字串"
description: "比較字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 920ee5e8-3d61-4941-b5af-fc50eaee427c
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 47ee37886fa2662a89730e9d52ee04987e37da2f
ms.lasthandoff: 03/02/2017

---

# <a name="comparing-strings"></a>比較字串

.NET 會提供數種方法來比較字串值。 下表列出並描述數值比較的方法。

方法名稱 | 用法
----------- | ---
[String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) | 比較兩個字串的值。 傳回整數值。
[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) | 比較兩個字串，而不考慮當地文化特性。 傳回整數值。
[String.CompareTo](xref:System.String.CompareTo(System.String)) | 比較目前字串物件與另一個字串。 傳回整數值。
[String.StartsWith](xref:System.String.StartsWith(System.String)) | 判斷字串是否以傳遞的字串開頭。 傳回布林值。
[String.EndsWith](xref:System.String.CompareTo(System.String)) | 判斷字串是否以傳遞的字串結束。 傳回布林值。
[String.Equals](xref:System.String.CompareTo(System.String)) | 判斷兩個字串是否相同。 傳回布林值。
[String.IndexOf](xref:System.String.IndexOf(System.Char)) | 從您正在檢查之字串的開頭開始，傳回字元或字串的索引位置。 傳回整數值。
[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) | 從您正在檢查之字串的結尾開始，傳回字元或字串的索引位置。 傳回整數值。

## <a name="compare"></a>比較

靜態 [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法提供全面的方式來比較兩個字串。 該方法會感知文化特性。 您可以使用這個函式來比較兩個字串或兩個字串的子字串。 此外，會假定多載為考慮或是忽略大小寫和文化特性變異數。 下表顯示這個方法可能會傳回的三個整數值。 

傳回值 | 條件
------------ | ---------
負整數 | 在此排序次序中，第一個字串在第二個字串的前面，或第一個字串為 `null`。
0 | 第一個字串和第二個字串相等，或兩個字串都為 `null`。
正整數或 1 | 在此排序次序中，第一個字串在第二個字串的後面，或第二個字串為 null。
 
> [!IMPORTANT]
> [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法主要是用於排序或字串排序時。 您不應該使用 [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) 方法。

下列範例會使用 [String.Compare](xref:System.String.Compare(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法，以判斷兩個字串的相對值。

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.Compare(string1, "Hello World?"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.Compare(string1, "Hello World?"))
```

此範例會顯示 `-1` 至主控台。

## <a name="compareordinal"></a>CompareOrdinal

[String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法會比較兩個字串物件，而不考慮當地文化特性。 這個方法的傳回值與上表中 `Compare` 方法所傳回的值相同。

> [!IMPORTANT]
> [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法主要是用於排序或字串排序時。 您不應該使用 [String.CompareOrdinal](xref:System.String.CompareOrdinal(System.String,System.Int32,System.String,System.Int32,System.Int32)) 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) 方法。

下列範例會使用 `CompareOrdinal` 方法來比較兩個字串的值。

```csharp
string string1 = "Hello World!";
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(String.CompareOrdinal(string1, "hello world!"))
```

此範例會顯示 `-32` 至主控台。

## <a name="compareto"></a>CompareTo

[String.CompareTo](xref:System.String.CompareTo(System.String)) 方法會比較目前字串物件封裝的字串和另一個字串或物件。 這個方法的傳回值與上表中 `String.Compare` 方法所傳回的值相同。

> [!IMPORTANT]
> [String.CompareTo](xref:System.String.CompareTo(System.String)) 方法主要是用於排序或字串排序時。 您不應該使用 [String.CompareTo](xref:System.String.CompareTo(System.String)) 方法來測試是否相等 (也就是明確地尋找為 0 的傳回值，而不考慮字串是否小於或大於另一個字串)。 相反地，若要判斷兩個字串是否相等，請使用 [String.Equals(String, String, StringComparison)](xref:System.String.Equals(System.String,System.String,System.StringComparison)) 方法。

下列範例會使用 `String.CompareTo` 方法來比較 `string1` 物件和 `string2` 物件。

```csharp
string string1 = "Hello World";
string string2 = "Hello World!";
int MyInt = string1.CompareTo(string2);
Console.WriteLine( MyInt );
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World!"
Dim MyInt As Integer = string1.CompareTo(string2)
Console.WriteLine(MyInt)
```

此範例會顯示 `-1` 至主控台。

## <a name="equals"></a>等於

[String.Equals](xref:System.String.CompareTo(System.String)) 方法可以輕易地判斷兩個字串是否相同。 這個區分大小寫的方法會傳回 `true` 或 `false` 布林值。 它可從現有的類別下使用，如下一個範例中所示。 下列範例會使用 `Equals` 方法來判斷字串物件是否包含片語 "Hello World"。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.Equals("Hello World"));
```

```vb
Dim string1 As String = "Hello World"
Console.WriteLine(string1.Equals("Hello World"))
```

此範例會顯示 `true` 至主控台。

這個方法也可用做為靜態方法。 下列範例會使用靜態方法來比較兩個字串物件。

```csharp
string string1 = "Hello World";
string string2 = "Hello World";
Console.WriteLine(String.Equals(string1, string2));
```

```vb
Dim string1 As String = "Hello World"
Dim string2 As String = "Hello World"
Console.WriteLine(String.Equals(string1, string2))
```

此範例會顯示 `true` 至主控台。

## <a name="startswith-and-endswith"></a>StartsWith 和 EndsWith

您可以使用 [String.StartsWith](xref:System.String.StartsWith(System.String)) 方法來判斷字串物件開頭是否為包含另一個字串的相同字元。 如果目前字串物件的開頭為傳遞的字串，則這個區分大小寫的方法會傳回 `true`，否則為 `false`。 下列範例會使用這個方法，以判斷字串物件開頭是否為 "Hello"。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.StartsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.StartsWith("Hello"))
```

此範例會顯示 `true` 至主控台。

[String.EndsWith](xref:System.String.CompareTo(System.String)) 方法會比較傳遞的字串和目前字串物件結尾上存在的字元。 它也會傳回布林值。 下列範例會使用 `EndsWith` 方法檢查字串結尾。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.EndsWith("Hello"));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.EndsWith("Hello"))
```

此範例會顯示 `false` 至主控台。

## <a name="indexof-and-lastindexof"></a>IndexOf 和 LastIndexOf

您可以使用 [String.IndexOf](xref:System.String.IndexOf(System.Char)) 方法，以判斷字串中第一次出現特定字元的位置。 這個區分大小寫的方法從字串開頭開始算起，並使用以零為起始的索引傳回傳遞字元的位置。 如果找不到該字元，則會傳回 –1 的值。

下列範例會使用 `IndexOf` 方法在字串中搜尋 '`l`' 的第一次出現位置。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.IndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.IndexOf("l"))
```

此範例會顯示 `2` 至主控台。

[String.LastIndexOf](xref:System.String.LastIndexOf(System.Char)) 方法類似 `String.IndexOf` 方法，只是它會傳回字串內特定字元最後一次出現的位置。 它會區分大小寫，並使用以零為起始的索引。 

下列範例會使用 `LastIndexOf` 方法在字串中搜尋 '`l`' 的最後一次出現位置。

```csharp
string string1 = "Hello World";
Console.WriteLine(string1.LastIndexOf('l'));
```

```vb
Dim string1 As String = "Hello World!"
Console.WriteLine(string1.LastIndexOf("l"))
```

此範例會顯示 `9` 至主控台。

當搭配 [String.Remove](xref:System.String.Remove(System.Int32)) 方法使用時，這兩種方法都很實用。 您可以使用 `IndexOf` 或 `LastIndexOf` 方法來擷取字元的位置，然後提供該位置給 `Remove method`，以移除字元或以該字元開頭的單字。

## <a name="see-also"></a>另請參閱

[基本字串作業](basic-string-operations.md)














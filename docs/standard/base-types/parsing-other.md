---
title: "在 .NET 中剖析其他字串"
description: "在 .NET 中剖析其他字串"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 67670b10-3df4-45ea-8908-5ba3f056887c
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: db80cc5f37e814f224ff76b14a906bb4d41064fb
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-other-strings-in-net"></a>在 .NET 中剖析其他字串

除了數值和 [DateTime](xref:System.DateTime) 字串，您也可以將表示 [Char](xref:System.Char)、[Boolean](xref:System.Boolean) 和 [Enum](xref:System.Enum) 類型的字串剖析成資料類型。

## <a name="char"></a>Char

與 [Char](xref:System.Char) 資料類型相關聯的靜態 parse 方法，可用於將包含單一字元的字串轉換成其 Unicode 值。 下列程式碼範例會將字串剖析成 Unicode 字元。

```csharp
string MyString1 = "A";
char MyChar = Char.Parse(MyString1);
// MyChar now contains a Unicode "A" character.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="boolean"></a>Boolean

[Boolean](xref:System.Boolean) 資料類型包含的 [Parse](xref:System.Boolean.Parse(System.String)) 方法，可用來將代表 `Boolean` 值的字串轉換成實際的 `Boolean` 類型。 這個方法不區分大小寫，而且可以成功剖析包含 "True" 或 "False" 的字串。 與 `Boolean` 類型相關聯的 `Parse` 方法也可剖析被空白字元包圍的字串。 如果傳遞任何其他字串，則會擲回 [FormatException](xref:System.FormatException)。

下面的程式碼範例會使用 `Parse` 方法將字串轉換成 `Boolean` 值。

```csharp
string MyString2 = "True";
bool MyBool = bool.Parse(MyString2);
// MyBool now contains a True Boolean value.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="enumeration"></a>列舉

您可以使用靜態的 [Parse](xref:System.Enum.Parse(System.Type,System.String)) 方法初始化字串值的列舉類型。 此方法接受您剖析的列舉類型、要剖析的字串，以及指出剖析是否區分大小寫的選擇性 `Boolean` 旗標。 您要剖析的字串可以包含數個以逗號分隔的值，前後可有一或多個空格 (也稱為空白字元)。 當字串包含多個值時，傳回物件的值就是結合了位元 OR 運算的所有指定值的值。

下例使用 `Parse` 方法，將字串表示轉換成列舉值。 [DayOfWeek](xref:System.DayOfWeek) 列舉會從字串初始化為星期四。

```csharp
string MyString3 = "Thursday";
DayOfWeek MyDays = (DayOfWeek)Enum.Parse(typeof(DayOfWeek), MyString3);
Console.WriteLine(MyDays);
// The result is Thursday.
```

```vb
Dim MyString3 As String = "Thursday"
Dim MyDays As DayOfWeek = CType([Enum].Parse(GetType(DayOfWeek), MyString3), DayOfWeek)
Console.WriteLine("{0:G}", MyDays)
' The result is Thursday.
```

## <a name="see-also"></a>另請參閱

[在 .NET 中剖析字串](parsing-strings.md)

[在 .NET 中格式化類型](formatting-types.md)

[在 .NET 中轉換類型](type-conversion.md)



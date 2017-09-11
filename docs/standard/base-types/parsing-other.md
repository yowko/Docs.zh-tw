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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: db80cc5f37e814f224ff76b14a906bb4d41064fb
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="55de4-104">在 .NET 中剖析其他字串</span><span class="sxs-lookup"><span data-stu-id="55de4-104">Parsing other strings in .NET</span></span>

<span data-ttu-id="55de4-105">除了數值和 [DateTime](xref:System.DateTime) 字串，您也可以將表示 [Char](xref:System.Char)、[Boolean](xref:System.Boolean) 和 [Enum](xref:System.Enum) 類型的字串剖析成資料類型。</span><span class="sxs-lookup"><span data-stu-id="55de4-105">In addition to numeric and [DateTime](xref:System.DateTime) strings, you can also parse strings that represent the types [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) into data types.</span></span>

## <a name="char"></a><span data-ttu-id="55de4-106">Char</span><span class="sxs-lookup"><span data-stu-id="55de4-106">Char</span></span>

<span data-ttu-id="55de4-107">與 [Char](xref:System.Char) 資料類型相關聯的靜態 parse 方法，可用於將包含單一字元的字串轉換成其 Unicode 值。</span><span class="sxs-lookup"><span data-stu-id="55de4-107">The static parse method associated with the [Char](xref:System.Char) data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="55de4-108">下列程式碼範例會將字串剖析成 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="55de4-108">The following code example parses a string into a Unicode character.</span></span>

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

## <a name="boolean"></a><span data-ttu-id="55de4-109">Boolean</span><span class="sxs-lookup"><span data-stu-id="55de4-109">Boolean</span></span>

<span data-ttu-id="55de4-110">[Boolean](xref:System.Boolean) 資料類型包含的 [Parse](xref:System.Boolean.Parse(System.String)) 方法，可用來將代表 `Boolean` 值的字串轉換成實際的 `Boolean` 類型。</span><span class="sxs-lookup"><span data-stu-id="55de4-110">The [Boolean](xref:System.Boolean) data type contains a [Parse](xref:System.Boolean.Parse(System.String)) method that you can use to convert a string that represents a `Boolean` value into an actual `Boolean` type.</span></span> <span data-ttu-id="55de4-111">這個方法不區分大小寫，而且可以成功剖析包含 "True" 或 "False" 的字串。</span><span class="sxs-lookup"><span data-stu-id="55de4-111">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="55de4-112">與 `Boolean` 類型相關聯的 `Parse` 方法也可剖析被空白字元包圍的字串。</span><span class="sxs-lookup"><span data-stu-id="55de4-112">The `Parse` method associated with the `Boolean` type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="55de4-113">如果傳遞任何其他字串，則會擲回 [FormatException](xref:System.FormatException)。</span><span class="sxs-lookup"><span data-stu-id="55de4-113">If any other string is passed, a [FormatException](xref:System.FormatException) is thrown.</span></span>

<span data-ttu-id="55de4-114">下面的程式碼範例會使用 `Parse` 方法將字串轉換成 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="55de4-114">The following code example uses the `Parse` method to convert a string into a `Boolean` value.</span></span>

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

## <a name="enumeration"></a><span data-ttu-id="55de4-115">列舉</span><span class="sxs-lookup"><span data-stu-id="55de4-115">Enumeration</span></span>

<span data-ttu-id="55de4-116">您可以使用靜態的 [Parse](xref:System.Enum.Parse(System.Type,System.String)) 方法初始化字串值的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="55de4-116">You can use the static [Parse](xref:System.Enum.Parse(System.Type,System.String)) method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="55de4-117">此方法接受您剖析的列舉類型、要剖析的字串，以及指出剖析是否區分大小寫的選擇性 `Boolean` 旗標。</span><span class="sxs-lookup"><span data-stu-id="55de4-117">This method accepts the enumeration type you are parsing, the string to parse, and an optional `Boolean` flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="55de4-118">您要剖析的字串可以包含數個以逗號分隔的值，前後可有一或多個空格 (也稱為空白字元)。</span><span class="sxs-lookup"><span data-stu-id="55de4-118">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="55de4-119">當字串包含多個值時，傳回物件的值就是結合了位元 OR 運算的所有指定值的值。</span><span class="sxs-lookup"><span data-stu-id="55de4-119">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>

<span data-ttu-id="55de4-120">下例使用 `Parse` 方法，將字串表示轉換成列舉值。</span><span class="sxs-lookup"><span data-stu-id="55de4-120">The following example uses the `Parse` method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="55de4-121">[DayOfWeek](xref:System.DayOfWeek) 列舉會從字串初始化為星期四。</span><span class="sxs-lookup"><span data-stu-id="55de4-121">The [DayOfWeek](xref:System.DayOfWeek) enumeration is initialized to Thursday from a string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="55de4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55de4-122">See Also</span></span>

[<span data-ttu-id="55de4-123">在 .NET 中剖析字串</span><span class="sxs-lookup"><span data-stu-id="55de4-123">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="55de4-124">在 .NET 中格式化類型</span><span class="sxs-lookup"><span data-stu-id="55de4-124">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="55de4-125">在 .NET 中轉換類型</span><span class="sxs-lookup"><span data-stu-id="55de4-125">Type conversion in .NET</span></span>](type-conversion.md)



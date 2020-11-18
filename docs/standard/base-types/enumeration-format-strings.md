---
title: 列舉格式字串
description: 使用 .NET 中的列舉. ToString 方法來建立列舉格式字串。 格式化列舉成員的數值、十六進位或字串值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: 02a12c36e47a82c15c01e578333e1c4465bab142
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829618"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="a1079-104">列舉格式字串</span><span class="sxs-lookup"><span data-stu-id="a1079-104">Enumeration format strings</span></span>

<span data-ttu-id="a1079-105">您可以使用 <xref:System.Enum.ToString%2A?displayProperty=nameWithType> 方法來建立新的字串物件，以表示列舉成員的數值、十六進位值或字串值。</span><span class="sxs-lookup"><span data-stu-id="a1079-105">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="a1079-106">這個方法會採用其中一個列舉格式字串，來指定您想要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="a1079-106">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="a1079-107">下列各節列出列舉格式字串及其傳回的值。</span><span class="sxs-lookup"><span data-stu-id="a1079-107">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="a1079-108">這些格式規範不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="a1079-108">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="a1079-109">G 或 g</span><span class="sxs-lookup"><span data-stu-id="a1079-109">G or g</span></span>

<span data-ttu-id="a1079-110">盡可能以字串值來顯示列舉項目；如果不可能，則會顯示目前執行個體的整數值。</span><span class="sxs-lookup"><span data-stu-id="a1079-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="a1079-111">如果列舉是使用 **Flags** 屬性集來定義，每個有效項目的字串值會串連在一起，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="a1079-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="a1079-112">如果未設定 **Flags** 屬性，則會以數值項目顯示無效的值。</span><span class="sxs-lookup"><span data-stu-id="a1079-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="a1079-113">下列範例說明 G 格式規範。</span><span class="sxs-lookup"><span data-stu-id="a1079-113">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="a1079-114">F 或 f</span><span class="sxs-lookup"><span data-stu-id="a1079-114">F or f</span></span>

<span data-ttu-id="a1079-115">盡可能以字串值來顯示列舉項目。</span><span class="sxs-lookup"><span data-stu-id="a1079-115">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="a1079-116">如果此值可完整顯示為列舉中的項目總合 (即使 **Flags** 屬性不存在)，每個有效項目的字串值會串連在一起，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="a1079-116">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="a1079-117">如果該值不完全取決於列舉項目，則會格式化為整數值。</span><span class="sxs-lookup"><span data-stu-id="a1079-117">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="a1079-118">下列範例說明 F 格式規範。</span><span class="sxs-lookup"><span data-stu-id="a1079-118">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="a1079-119">D 或 d</span><span class="sxs-lookup"><span data-stu-id="a1079-119">D or d</span></span>

<span data-ttu-id="a1079-120">盡可能以最短的整數值表示來顯示列舉項目。</span><span class="sxs-lookup"><span data-stu-id="a1079-120">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="a1079-121">下列範例說明 D 格式規範。</span><span class="sxs-lookup"><span data-stu-id="a1079-121">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="a1079-122">X 或 x</span><span class="sxs-lookup"><span data-stu-id="a1079-122">X or x</span></span>

<span data-ttu-id="a1079-123">以十六進位值來顯示列舉項目。</span><span class="sxs-lookup"><span data-stu-id="a1079-123">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="a1079-124">值在必要的情況下會以前置零來表示，以確保結果字串使用兩個字元代表列舉類型之[底層數值類型](xref:System.Enum.GetUnderlyingType%2A)每個位元組。</span><span class="sxs-lookup"><span data-stu-id="a1079-124">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="a1079-125">下列範例說明 X 格式規範。</span><span class="sxs-lookup"><span data-stu-id="a1079-125">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="a1079-126">在範例中，<xref:System.ConsoleColor> 與 <xref:System.IO.FileAttributes> 兩者的底層類型是 <xref:System.Int32>，或 32 位元 (或 4 位元) 整數，這會產生 8 個字元的結果字串。</span><span class="sxs-lookup"><span data-stu-id="a1079-126">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="a1079-127">範例</span><span class="sxs-lookup"><span data-stu-id="a1079-127">Example</span></span>

<span data-ttu-id="a1079-128">下列範例會定義名為 `Colors` 的列舉，該列舉是由三個項目所組成︰`Red`、`Blue` 和 `Green`。</span><span class="sxs-lookup"><span data-stu-id="a1079-128">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="a1079-129">定義列舉之後，可利用下列方式宣告執行個體。</span><span class="sxs-lookup"><span data-stu-id="a1079-129">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="a1079-130">然後可使用 `Color.ToString(System.String)` 方法，根據傳遞給列舉值的格式規範，以不同的方式來顯示列舉值。</span><span class="sxs-lookup"><span data-stu-id="a1079-130">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="a1079-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1079-131">See also</span></span>

- [<span data-ttu-id="a1079-132">格式化類型</span><span class="sxs-lookup"><span data-stu-id="a1079-132">Formatting Types</span></span>](formatting-types.md)

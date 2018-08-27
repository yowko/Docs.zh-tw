---
title: 列舉格式字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4402bf58ea853d8a373592eec274a8bf75e7e90c
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925738"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="224ee-102">列舉格式字串</span><span class="sxs-lookup"><span data-stu-id="224ee-102">Enumeration Format Strings</span></span>
<span data-ttu-id="224ee-103">您可以使用 <xref:System.Enum.ToString%2A?displayProperty=nameWithType> 方法來建立新的字串物件，以表示列舉成員的數值、十六進位值或字串值。</span><span class="sxs-lookup"><span data-stu-id="224ee-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="224ee-104">這個方法會採用其中一個列舉格式字串，來指定您想要傳回的值。</span><span class="sxs-lookup"><span data-stu-id="224ee-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="224ee-105">下表列出列舉格式字串及其傳回的值。</span><span class="sxs-lookup"><span data-stu-id="224ee-105">The following table lists the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="224ee-106">這些格式規範不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="224ee-106">These format specifiers are not case-sensitive.</span></span>

| <span data-ttu-id="224ee-107">格式化字串</span><span class="sxs-lookup"><span data-stu-id="224ee-107">Format string</span></span> | <span data-ttu-id="224ee-108">結果</span><span class="sxs-lookup"><span data-stu-id="224ee-108">Result</span></span> |
| ------------- | ------ |
| <span data-ttu-id="224ee-109">G 或 g</span><span class="sxs-lookup"><span data-stu-id="224ee-109">G or g</span></span> | <span data-ttu-id="224ee-110">盡可能以字串值來顯示列舉項目；如果不可能，則會顯示目前執行個體的整數值。</span><span class="sxs-lookup"><span data-stu-id="224ee-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="224ee-111">如果列舉是使用 **Flags** 屬性集來定義，每個有效項目的字串值會串連在一起，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="224ee-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="224ee-112">如果未設定 **Flags** 屬性，則會以數值項目顯示無效的值。</span><span class="sxs-lookup"><span data-stu-id="224ee-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="224ee-113">下列範例說明 G 格式規範。</span><span class="sxs-lookup"><span data-stu-id="224ee-113">The following example illustrates the G format specifier.</span></span><br /><br /><span data-ttu-id="224ee-114">[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="224ee-114">[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]</span></span> |
| <span data-ttu-id="224ee-115">F 或 f</span><span class="sxs-lookup"><span data-stu-id="224ee-115">F or f</span></span> | <span data-ttu-id="224ee-116">盡可能以字串值來顯示列舉項目。</span><span class="sxs-lookup"><span data-stu-id="224ee-116">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="224ee-117">如果此值可完整顯示為列舉中的項目總合 (即使 **Flags** 屬性不存在)，每個有效項目的字串值會串連在一起，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="224ee-117">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="224ee-118">如果該值不完全取決於列舉項目，則會格式化為整數值。</span><span class="sxs-lookup"><span data-stu-id="224ee-118">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="224ee-119">下列範例說明 F 格式規範。</span><span class="sxs-lookup"><span data-stu-id="224ee-119">The following example illustrates the F format specifier.</span></span><br /><br /><span data-ttu-id="224ee-120">[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="224ee-120">[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]</span></span> |
| <span data-ttu-id="224ee-121">D 或 d</span><span class="sxs-lookup"><span data-stu-id="224ee-121">D or d</span></span> | <span data-ttu-id="224ee-122">盡可能以最短的整數值表示來顯示列舉項目。</span><span class="sxs-lookup"><span data-stu-id="224ee-122">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="224ee-123">下列範例說明 D 格式規範。</span><span class="sxs-lookup"><span data-stu-id="224ee-123">The following example illustrates the D format specifier.</span></span><br /><br /><span data-ttu-id="224ee-124">[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="224ee-124">[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]</span></span> |
| <span data-ttu-id="224ee-125">X 或 x</span><span class="sxs-lookup"><span data-stu-id="224ee-125">X or x</span></span> | <span data-ttu-id="224ee-126">以十六進位值來顯示列舉項目。</span><span class="sxs-lookup"><span data-stu-id="224ee-126">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="224ee-127">該值可視需要加上前置零來表示，以確保值的長度至少有八位數。</span><span class="sxs-lookup"><span data-stu-id="224ee-127">The value is represented with leading zeros as necessary, to ensure that the value is a minimum eight digits in length.</span></span> <span data-ttu-id="224ee-128">下列範例說明 X 格式規範。</span><span class="sxs-lookup"><span data-stu-id="224ee-128">The following example illustrates the X format specifier.</span></span><br /><br /> <span data-ttu-id="224ee-129">[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="224ee-129">[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]</span></span> |

## <a name="example"></a><span data-ttu-id="224ee-130">範例</span><span class="sxs-lookup"><span data-stu-id="224ee-130">Example</span></span>

<span data-ttu-id="224ee-131">下列範例會定義名為 `Colors` 的列舉，該列舉是由三個項目所組成︰`Red`、`Blue` 和 `Green`。</span><span class="sxs-lookup"><span data-stu-id="224ee-131">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="224ee-132">定義列舉之後，可利用下列方式宣告執行個體。</span><span class="sxs-lookup"><span data-stu-id="224ee-132">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="224ee-133">然後可使用 `Color.ToString(System.String)` 方法，根據傳遞給列舉值的格式規範，以不同的方式來顯示列舉值。</span><span class="sxs-lookup"><span data-stu-id="224ee-133">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="224ee-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="224ee-134">See Also</span></span>

[<span data-ttu-id="224ee-135">格式化類型</span><span class="sxs-lookup"><span data-stu-id="224ee-135">Formatting Types</span></span>](formatting-types.md)
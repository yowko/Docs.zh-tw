---
title: "在 .NET 中剖析字串"
description: "在 .NET 中剖析字串"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: c741ae793d491f691a355df6ad064b81d609c7e5
ms.contentlocale: zh-tw
ms.lasthandoff: 03/03/2017

---

# <a name="parsing-strings-in-net"></a><span data-ttu-id="5fd36-104">在 .NET 中剖析字串</span><span class="sxs-lookup"><span data-stu-id="5fd36-104">Parsing strings in .NET</span></span>

<span data-ttu-id="5fd36-105">剖析作業會將代表 .NET 基底類型的字串轉換成該基底類型。</span><span class="sxs-lookup"><span data-stu-id="5fd36-105">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="5fd36-106">例如，剖析作業用來將字串轉換為浮點數或日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="5fd36-106">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="5fd36-107">最常用來執行剖析作業的方法是 `Parse` 方法。</span><span class="sxs-lookup"><span data-stu-id="5fd36-107">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="5fd36-108">因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。</span><span class="sxs-lookup"><span data-stu-id="5fd36-108">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="5fd36-109">當格式化使用實作 [IFormatProvider](xref:System.IFormatProvider) 介面的物件提供區分文化特性的格式資訊時，剖析也會使用實作 [IFormatProvider](xref:System.IFormatProvider) 介面的物件判斷如何解譯字串表示。</span><span class="sxs-lookup"><span data-stu-id="5fd36-109">Just as formatting uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to provide culture-sensitive formatting information, parsing also uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="5fd36-110">如需詳細資訊，請參閱[在 .NET 中格式化類型](formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5fd36-110">For more information, see [Formatting Types in .NET](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5fd36-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="5fd36-111">In This Section</span></span>

<span data-ttu-id="5fd36-112">[在 .NET 中剖析數值字串](parsing-numeric.md)：說明如何將字串轉換成 .NET 數值類型。</span><span class="sxs-lookup"><span data-stu-id="5fd36-112">[Parsing Numeric Strings in .NET](parsing-numeric.md) - Describes how to convert strings into .NET numeric types.</span></span>

<span data-ttu-id="5fd36-113">[在 .NET 中剖析日期和時間字串](parsing-datetime.md)：說明如何將字串轉換成 .NET `DateTime` 類型。</span><span class="sxs-lookup"><span data-stu-id="5fd36-113">[Parsing Date and Time Strings in .NET](parsing-datetime.md) - Describes how to convert strings into .NET `DateTime` types.</span></span>

<span data-ttu-id="5fd36-114">[在 .NET 中剖析其他字串](parsing-other.md)：說明如何將字串轉換成 [Char](xref:System.Char)、[Boolean](xref:System.Boolean) 和 [Enum](xref:System.Enum) 類型。</span><span class="sxs-lookup"><span data-stu-id="5fd36-114">[Parsing Other Strings in .NET](parsing-other.md) - Describes how to convert strings into [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) types.</span></span>

<span data-ttu-id="5fd36-115">[在 .NET 中格式化類型](formatting-types.md)：描述基本的格式化概念，例如格式規範和格式提供者。</span><span class="sxs-lookup"><span data-stu-id="5fd36-115">[Formatting Types in .NET](formatting-types.md) - Describes basic formatting concepts like format specifiers and format providers.</span></span>

<span data-ttu-id="5fd36-116">[.NET 口的類型轉換](type-conversion.md)：說明如何轉換類型。</span><span class="sxs-lookup"><span data-stu-id="5fd36-116">[Type Conversion in .NET](type-conversion.md) - Describes how to convert types.</span></span>

<span data-ttu-id="5fd36-117">[在 .NET 中使用基底類型](index.md)：說明您可以對 .NET 基底類型執行的一般作業。</span><span class="sxs-lookup"><span data-stu-id="5fd36-117">[Working with Base Types in .NET](index.md) - Describes common operations that you can perform on .NET base types.</span></span>



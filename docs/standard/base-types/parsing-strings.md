---
title: 將字串轉換成類型
description: 瞭解 .NET 中的字串剖析。 剖析會將代表 .NET 基底類型的字串轉換成該基底類型。 剖析是格式化的反向操作。
ms.date: 03/30/2017
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 8fbfe8596e49ed101ea7d6bb65298e432a6fac13
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821901"
---
# <a name="parse-strings-in-net"></a><span data-ttu-id="2e51b-105">在 .NET 中剖析字串</span><span class="sxs-lookup"><span data-stu-id="2e51b-105">Parse strings in .NET</span></span>

<span data-ttu-id="2e51b-106">*剖析* 作業會將代表 .net 基底類型的字串轉換成該基底類型。</span><span class="sxs-lookup"><span data-stu-id="2e51b-106">A *parsing* operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="2e51b-107">例如，剖析作業會用來將字串轉換成浮點數或日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="2e51b-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date-and-time value.</span></span> <span data-ttu-id="2e51b-108">最常用來執行剖析作業的方法是 `Parse` 方法。</span><span class="sxs-lookup"><span data-stu-id="2e51b-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="2e51b-109">因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。</span><span class="sxs-lookup"><span data-stu-id="2e51b-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="2e51b-110">就像格式化會使用實作 <xref:System.IFormatProvider> 介面的物件來提供區分文化特性的格式化資訊，剖析也會使用實作 <xref:System.IFormatProvider> 介面的物件來判斷如何解譯字串表示。</span><span class="sxs-lookup"><span data-stu-id="2e51b-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="2e51b-111">如需詳細資訊，請參閱 [格式類型](formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2e51b-111">For more information, see [Format types](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2e51b-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="2e51b-112">In This Section</span></span>
 <span data-ttu-id="2e51b-113">[剖析數值字串](parsing-numeric.md)</span><span class="sxs-lookup"><span data-stu-id="2e51b-113">[Parsing Numeric Strings](parsing-numeric.md)</span></span>\
 <span data-ttu-id="2e51b-114">描述如何將字串轉換成 .NET 數值類型。</span><span class="sxs-lookup"><span data-stu-id="2e51b-114">Describes how to convert strings into .NET numeric types.</span></span>

 <span data-ttu-id="2e51b-115">[剖析日期和時間字串](parsing-datetime.md)</span><span class="sxs-lookup"><span data-stu-id="2e51b-115">[Parsing Date and Time Strings](parsing-datetime.md)</span></span>\
 <span data-ttu-id="2e51b-116">描述如何將字串轉換成 .NET **DateTime** 類型。</span><span class="sxs-lookup"><span data-stu-id="2e51b-116">Describes how to convert strings into .NET **DateTime** types.</span></span>

 <span data-ttu-id="2e51b-117">[剖析其他字串](parsing-other.md)</span><span class="sxs-lookup"><span data-stu-id="2e51b-117">[Parsing Other Strings](parsing-other.md)</span></span>\
 <span data-ttu-id="2e51b-118">描述如何將字串轉換成 **Char**、**Boolean** 和 **Enum** 類型。</span><span class="sxs-lookup"><span data-stu-id="2e51b-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>

## <a name="related-sections"></a><span data-ttu-id="2e51b-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="2e51b-119">Related Sections</span></span>
 <span data-ttu-id="2e51b-120">[格式化類型](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="2e51b-120">[Formatting Types](formatting-types.md)</span></span>\
 <span data-ttu-id="2e51b-121">描述基本的格式化概念，例如格式規範和格式提供者。</span><span class="sxs-lookup"><span data-stu-id="2e51b-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>

 <span data-ttu-id="2e51b-122">[.NET 中的類型轉換](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="2e51b-122">[Type Conversion in .NET](type-conversion.md)</span></span>\
 <span data-ttu-id="2e51b-123">描述如何轉換類型。</span><span class="sxs-lookup"><span data-stu-id="2e51b-123">Describes how to convert types.</span></span>

---
title: 在 DateTime 與 DateTimeOffset 之間轉換
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime structure, converting
- time zones [.NET Framework], conversions
- UTC times, converting
- DateTimeOffset structure, converting
- converting DateTimeOffset and DateTime values
- dates [.NET Framework], converting
- converting times
- Date data type, converting
- local time conversions
ms.assetid: b605ff97-0c45-4c24-833f-4c6a3e8be64c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4bce84d26e8f498f065c887b583e18d8ea7c786
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651197"
---
# <a name="converting-between-datetime-and-datetimeoffset"></a><span data-ttu-id="cc6cc-102">在 DateTime 與 DateTimeOffset 之間轉換</span><span class="sxs-lookup"><span data-stu-id="cc6cc-102">Converting between DateTime and DateTimeOffset</span></span>

<span data-ttu-id="cc6cc-103">雖然<xref:System.DateTimeOffset>結構提供更高的時區感知<xref:System.DateTime>結構，<xref:System.DateTime>更常在方法呼叫中使用參數。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-103">Although the <xref:System.DateTimeOffset> structure provides a greater degree of time zone awareness than the <xref:System.DateTime> structure, <xref:System.DateTime> parameters are used more commonly in method calls.</span></span> <span data-ttu-id="cc6cc-104">因此，要轉換的能力<xref:System.DateTimeOffset>值來<xref:System.DateTime>值和相反作業特別重要。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-104">Because of this, the ability to convert <xref:System.DateTimeOffset> values to <xref:System.DateTime> values and vice versa is particularly important.</span></span> <span data-ttu-id="cc6cc-105">本主題說明如何執行這些轉換會保留盡可能最多時區資訊的方式。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-105">This topic shows how to perform these conversions in a way that preserves as much time zone information as possible.</span></span>

> [!NOTE]
> <span data-ttu-id="cc6cc-106">同時<xref:System.DateTime>而<xref:System.DateTimeOffset>類型代表時區時間時，有一些限制。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-106">Both the <xref:System.DateTime> and the <xref:System.DateTimeOffset> types have some limitations when representing times in time zones.</span></span> <span data-ttu-id="cc6cc-107">使用其<xref:System.DateTime.Kind%2A>屬性，<xref:System.DateTime>能夠反映只有 Coordinated Universal Time (UTC) 和系統的當地時區。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-107">With its <xref:System.DateTime.Kind%2A> property, <xref:System.DateTime> is able to reflect only Coordinated Universal Time (UTC) and the system's local time zone.</span></span> <span data-ttu-id="cc6cc-108"><xref:System.DateTimeOffset> 會反映與 UTC 之位移的時間，但它不會反映屬於實際時區的時差。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-108"><xref:System.DateTimeOffset> reflects a time's offset from UTC, but it does not reflect the actual time zone to which that offset belongs.</span></span> <span data-ttu-id="cc6cc-109">如需時間值以及時區支援的詳細資訊，請參閱[選擇 DateTime、 DateTimeOffset、 TimeSpan 和 TimeZoneInfo 之間](../../../docs/standard/datetime/choosing-between-datetime.md)。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-109">For details about time values and support for time zones, see [Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md).</span></span>

## <a name="conversions-from-datetime-to-datetimeoffset"></a><span data-ttu-id="cc6cc-110">從 DateTime 到 DateTimeOffset 的轉換</span><span class="sxs-lookup"><span data-stu-id="cc6cc-110">Conversions from DateTime to DateTimeOffset</span></span>

<span data-ttu-id="cc6cc-111"><xref:System.DateTimeOffset>結構提供兩個對等的方式來執行<xref:System.DateTime>到<xref:System.DateTimeOffset>適用於大部分轉換的轉換：</span><span class="sxs-lookup"><span data-stu-id="cc6cc-111">The <xref:System.DateTimeOffset> structure provides two equivalent ways to perform <xref:System.DateTime> to <xref:System.DateTimeOffset> conversion that are suitable for most conversions:</span></span>

* <span data-ttu-id="cc6cc-112"><xref:System.DateTimeOffset.%23ctor%2A>建構函式，建立新<xref:System.DateTimeOffset>物件，根據<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-112">The <xref:System.DateTimeOffset.%23ctor%2A> constructor, which creates a new <xref:System.DateTimeOffset> object based on a <xref:System.DateTime> value.</span></span>

* <span data-ttu-id="cc6cc-113">隱含轉換運算子，可讓您指派<xref:System.DateTime>值<xref:System.DateTimeOffset>物件。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-113">The implicit conversion operator, which allows you to assign a <xref:System.DateTime> value to a <xref:System.DateTimeOffset> object.</span></span>

<span data-ttu-id="cc6cc-114">針對 UTC 和當地<xref:System.DateTime>值，<xref:System.DateTimeOffset.Offset%2A>屬性產生<xref:System.DateTimeOffset>精確地反映 UTC 或本地時間的時區時差。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-114">For UTC and local <xref:System.DateTime> values, the <xref:System.DateTimeOffset.Offset%2A> property of the resulting <xref:System.DateTimeOffset> value accurately reflects the UTC or local time zone offset.</span></span> <span data-ttu-id="cc6cc-115">例如，下列程式碼會將 UTC 時間轉換成其對等<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-115">For example, the following code converts a UTC time to its equivalent <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#1)]

<span data-ttu-id="cc6cc-116">在此情況下，`utcTime2` 變數的位移是 00:00。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-116">In this case, the offset of the `utcTime2` variable is 00:00.</span></span> <span data-ttu-id="cc6cc-117">同樣地，下列程式碼會將當地時間轉換成其對等<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-117">Similarly, the following code converts a local time to its equivalent <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#2)]

<span data-ttu-id="cc6cc-118">不過，為了<xref:System.DateTime>值的<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，這些兩種轉換方法會產生<xref:System.DateTimeOffset>位移為本地時區的值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-118">However, for <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, these two conversion methods produce a <xref:System.DateTimeOffset> value whose offset is that of the local time zone.</span></span> <span data-ttu-id="cc6cc-119">下列範例會示範以下列時區執行的情況：太平洋標準時區。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-119">This is shown in the following example, which is run in the U.S. Pacific Standard Time zone.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#3)]

<span data-ttu-id="cc6cc-120">如果<xref:System.DateTime>值的日期和時間的事物當地時區或 UTC 以外，您可以將它轉換成<xref:System.DateTimeOffset>值，並保留其時區資訊呼叫多載<xref:System.DateTimeOffset.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-120">If the <xref:System.DateTime> value reflects the date and time in something other than the local time zone or UTC, you can convert it to a <xref:System.DateTimeOffset> value and preserve its time zone information by calling the overloaded <xref:System.DateTimeOffset.%23ctor%2A> constructor.</span></span> <span data-ttu-id="cc6cc-121">例如，下列範例會具現化<xref:System.DateTimeOffset>反映中部標準時間的物件。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-121">For example, the following example instantiates a <xref:System.DateTimeOffset> object that reflects Central Standard Time.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#4)]

<span data-ttu-id="cc6cc-122">這個建構函式多載中，第二個參數<xref:System.TimeSpan>從其中擷取物件，表示 UTC 時間的位移，藉由呼叫<xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType>方法對應時區的時間。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-122">The second parameter to this constructor overload, a <xref:System.TimeSpan> object that represents the time's offset from UTC, should be retrieved by calling the <xref:System.TimeZoneInfo.GetUtcOffset%28System.DateTime%29?displayProperty=nameWithType> method of the time's corresponding time zone.</span></span> <span data-ttu-id="cc6cc-123">方法的單一參數是<xref:System.DateTime>值，表示要轉換的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-123">The method's single parameter is the <xref:System.DateTime> value that represents the date and time to be converted.</span></span> <span data-ttu-id="cc6cc-124">如果時區支援日光節約時間，則此參數允許這個方法來判斷該特定日期和時間的適當位移。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-124">If the time zone supports daylight saving time, this parameter allows the method to determine the appropriate offset for that particular date and time.</span></span>

## <a name="conversions-from-datetimeoffset-to-datetime"></a><span data-ttu-id="cc6cc-125">從 DateTimeOffset 到 DateTime 的轉換</span><span class="sxs-lookup"><span data-stu-id="cc6cc-125">Conversions from DateTimeOffset to DateTime</span></span>

<span data-ttu-id="cc6cc-126"><xref:System.DateTimeOffset.DateTime%2A>屬性最常用來執行<xref:System.DateTimeOffset>到<xref:System.DateTime>轉換。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-126">The <xref:System.DateTimeOffset.DateTime%2A> property is most commonly used to perform <xref:System.DateTimeOffset> to <xref:System.DateTime> conversion.</span></span> <span data-ttu-id="cc6cc-127">不過，它會傳回<xref:System.DateTime>值<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Unspecified>，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-127">However, it returns a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified>, as the following example illustrates.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#5)]

<span data-ttu-id="cc6cc-128">這表示任何資訊的相關<xref:System.DateTimeOffset>轉換會遺失值的關聯性為 UTC 時<xref:System.DateTimeOffset.DateTime%2A>屬性使用。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-128">This means that any information about the <xref:System.DateTimeOffset> value's relationship to UTC is lost by the conversion when the <xref:System.DateTimeOffset.DateTime%2A> property is used.</span></span> <span data-ttu-id="cc6cc-129">這會影響<xref:System.DateTimeOffset>值，對應至 UTC 時間或系統的當地時間，因為<xref:System.DateTimeOffset.DateTime%2A>結構會反映只有這兩個時區中其<xref:System.DateTime.Kind%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-129">This affects <xref:System.DateTimeOffset> values that correspond to UTC time or to the system's local time because the <xref:System.DateTimeOffset.DateTime%2A> structure reflects only those two time zones in its <xref:System.DateTime.Kind%2A> property.</span></span>

<span data-ttu-id="cc6cc-130">轉換時，保留最多時區資訊，盡可能<xref:System.DateTimeOffset>要<xref:System.DateTime>值，您可以使用<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>和<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-130">To preserve as much time zone information as possible when converting a <xref:System.DateTimeOffset> to a <xref:System.DateTime> value, you can use the <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> properties.</span></span>

### <a name="converting-a-utc-time"></a><span data-ttu-id="cc6cc-131">轉換 UTC 時間</span><span class="sxs-lookup"><span data-stu-id="cc6cc-131">Converting a UTC time</span></span>

<span data-ttu-id="cc6cc-132">表示已轉換<xref:System.DateTimeOffset.DateTime%2A>值是 UTC 時間，您可以擷取的值<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-132">To indicate that a converted <xref:System.DateTimeOffset.DateTime%2A> value is the UTC time, you can retrieve the value of the <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="cc6cc-133">不同於<xref:System.DateTimeOffset.DateTime%2A>屬性有兩種：</span><span class="sxs-lookup"><span data-stu-id="cc6cc-133">It differs from the <xref:System.DateTimeOffset.DateTime%2A> property in two ways:</span></span>

* <span data-ttu-id="cc6cc-134">它會傳回<xref:System.DateTime>值<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Utc>。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-134">It returns a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span>

* <span data-ttu-id="cc6cc-135">如果<xref:System.DateTimeOffset.Offset%2A>屬性值不等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>，它會將時間轉換為 UTC。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-135">If the <xref:System.DateTimeOffset.Offset%2A> property value does not equal <xref:System.TimeSpan.Zero?displayProperty=nameWithType>, it converts the time to UTC.</span></span>

> [!NOTE]
> <span data-ttu-id="cc6cc-136">如果您的應用程式需要轉換<xref:System.DateTime>值明確地識別單一點時間，您應該考慮使用<xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType>屬性來處理所有<xref:System.DateTimeOffset>到<xref:System.DateTime>轉換。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-136">If your application requires that converted <xref:System.DateTime> values unambiguously identify a single point in time, you should consider using the <xref:System.DateTimeOffset.UtcDateTime%2A?displayProperty=nameWithType> property to handle all <xref:System.DateTimeOffset> to <xref:System.DateTime> conversions.</span></span>

<span data-ttu-id="cc6cc-137">下列程式碼會使用<xref:System.DateTimeOffset.UtcDateTime%2A>要轉換的屬性<xref:System.DateTimeOffset>位移等於的值<xref:System.TimeSpan.Zero?displayProperty=nameWithType>到<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-137">The following code uses the <xref:System.DateTimeOffset.UtcDateTime%2A> property to convert a <xref:System.DateTimeOffset> value whose offset equals <xref:System.TimeSpan.Zero?displayProperty=nameWithType> to a <xref:System.DateTime> value.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#6)]

<span data-ttu-id="cc6cc-138">下列程式碼會使用<xref:System.DateTimeOffset.UtcDateTime%2A>屬性上執行時區轉換和型別轉換<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-138">The following code uses the <xref:System.DateTimeOffset.UtcDateTime%2A> property to perform both a time zone conversion and a type conversion on a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#12)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#12)]

### <a name="converting-a-local-time"></a><span data-ttu-id="cc6cc-139">轉換當地時間</span><span class="sxs-lookup"><span data-stu-id="cc6cc-139">Converting a local time</span></span>

<span data-ttu-id="cc6cc-140">表示<xref:System.DateTimeOffset>值代表當地時間，您可以傳遞<xref:System.DateTime>所傳回的值<xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType>屬性設`static`(`Shared`在 Visual Basic 中)<xref:System.DateTime.SpecifyKind%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-140">To indicate that a <xref:System.DateTimeOffset> value represents the local time, you can pass the <xref:System.DateTime> value returned by the <xref:System.DateTimeOffset.DateTime%2A?displayProperty=nameWithType> property to the `static` (`Shared` in Visual Basic) <xref:System.DateTime.SpecifyKind%2A> method.</span></span> <span data-ttu-id="cc6cc-141">此方法傳回的日期和時間做為其第一個參數，傳遞給它，但設定<xref:System.DateTime.Kind%2A>屬性設為其第二個參數所指定的值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-141">The method returns the date and time passed to it as its first parameter, but sets the <xref:System.DateTime.Kind%2A> property to the value specified by its second parameter.</span></span> <span data-ttu-id="cc6cc-142">下列程式碼會使用<xref:System.DateTime.SpecifyKind%2A>方法轉換時<xref:System.DateTimeOffset>其位移對應至當地時區的值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-142">The following code uses the <xref:System.DateTime.SpecifyKind%2A> method when converting a <xref:System.DateTimeOffset> value whose offset corresponds to that of the local time zone.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#7)]

<span data-ttu-id="cc6cc-143">您也可以使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>要轉換的屬性<xref:System.DateTimeOffset>值，以本機<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-143">You can also use the <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> property to convert a <xref:System.DateTimeOffset> value to a local <xref:System.DateTime> value.</span></span> <span data-ttu-id="cc6cc-144"><xref:System.DateTime.Kind%2A>屬性傳回之<xref:System.DateTime>值是<xref:System.DateTimeKind.Local>。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-144">The <xref:System.DateTime.Kind%2A> property of the returned <xref:System.DateTime> value is <xref:System.DateTimeKind.Local>.</span></span> <span data-ttu-id="cc6cc-145">下列程式碼會使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>轉換時的屬性<xref:System.DateTimeOffset>其位移對應至當地時區的值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-145">The following code uses the <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> property when converting a <xref:System.DateTimeOffset> value whose offset corresponds to that of the local time zone.</span></span> 

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#10)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#10)]

<span data-ttu-id="cc6cc-146">當您擷取<xref:System.DateTime>值使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性，屬性的`get`存取子會先轉換<xref:System.DateTimeOffset>值為 UTC，然後將它轉換為當地時間藉由呼叫<xref:System.DateTimeOffset.ToLocalTime%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-146">When you retrieve a <xref:System.DateTime> value using the <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> property, the property's `get` accessor first converts the <xref:System.DateTimeOffset> value to UTC, then converts it to local time by calling the <xref:System.DateTimeOffset.ToLocalTime%2A> method.</span></span> <span data-ttu-id="cc6cc-147">這表示，您可以擷取值，以從<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>執行時區轉換，在此同時，您會執行類型轉換的屬性。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-147">This means that you can retrieve a value from the <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> property to perform a time zone conversion at the same time that you perform a type conversion.</span></span> <span data-ttu-id="cc6cc-148">這也表示執行轉換時會套用當地時區的調整規則。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-148">It also means that the local time zone's adjustment rules are applied in performing the conversion.</span></span> <span data-ttu-id="cc6cc-149">下列程式碼說明如何使用<xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType>屬性，來執行類型和時區轉換。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-149">The following code illustrates the use of the <xref:System.DateTimeOffset.LocalDateTime%2A?displayProperty=nameWithType> property to perform both a type and a time zone conversion.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#11)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#11)]

### <a name="a-general-purpose-conversion-method"></a><span data-ttu-id="cc6cc-150">一般用途的轉換方法</span><span class="sxs-lookup"><span data-stu-id="cc6cc-150">A general-purpose conversion method</span></span>

<span data-ttu-id="cc6cc-151">下列範例會定義名為的方法`ConvertFromDateTimeOffset`以將轉換成<xref:System.DateTimeOffset>值來<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-151">The following example defines a method named `ConvertFromDateTimeOffset` that converts <xref:System.DateTimeOffset> values to <xref:System.DateTime> values.</span></span> <span data-ttu-id="cc6cc-152">根據其位移，它會判斷是否<xref:System.DateTimeOffset>值為 UTC 時間、 當地時間或一些其他的時間，並定義傳回的日期和時間值的<xref:System.DateTime.Kind%2A>屬性據此。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-152">Based on its offset, it determines whether the <xref:System.DateTimeOffset> value is a UTC time, a local time, or some other time, and defines the returned date and time value's <xref:System.DateTime.Kind%2A> property accordingly.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#8)]

<span data-ttu-id="cc6cc-153">下列範例會呼叫`ConvertFromDateTimeOffset`方法，將轉換<xref:System.DateTimeOffset>值代表 UTC 時間、 當地時間，以及位於美國的時間中央標準時區時間。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-153">The follow example calls the `ConvertFromDateTimeOffset` method to convert <xref:System.DateTimeOffset> values that represent a UTC time, a local time, and a time in the U.S. Central Standard Time zone.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/cs/Conversions.cs#9)]
[!code-vb[System.DateTimeOffset.Conceptual.Conversions#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Conversions/vb/Conversions.vb#9)]

<span data-ttu-id="cc6cc-154">請注意，此程式碼有兩個假設，而且根據日期和時間值的套用和來源可能不一定有效︰</span><span class="sxs-lookup"><span data-stu-id="cc6cc-154">Note that this code makes two assumptions that, depending on the application and the source of its date and time values, may not always be valid:</span></span>

* <span data-ttu-id="cc6cc-155">它會假設日期和時間值的位移是<xref:System.TimeSpan.Zero?displayProperty=nameWithType>代表 UTC。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-155">It assumes that a date and time value whose offset is <xref:System.TimeSpan.Zero?displayProperty=nameWithType> represents UTC.</span></span> <span data-ttu-id="cc6cc-156">事實上，UTC 不是特定時區的時間，而是相對於標準化全世界時區時間的時間。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-156">In fact, UTC is not a time in a particular time zone, but the time in relation to which the times in the world's time zones are standardized.</span></span> <span data-ttu-id="cc6cc-157">時區也可以有的位移<xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-157">Time zones can also have an offset of <xref:System.TimeSpan.Zero>.</span></span>

* <span data-ttu-id="cc6cc-158">它假設位移等於當地時區位移的日期和時間代表當地時區。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-158">It assumes that a date and time whose offset equals that of the local time zone represents the local time zone.</span></span> <span data-ttu-id="cc6cc-159">因為日期和時間值與其原始時區解除關聯，所以這可能不是這種情況；日期和時間可能源自另一個具有相同位移的時區。</span><span class="sxs-lookup"><span data-stu-id="cc6cc-159">Because date and time values are disassociated from their original time zone, this may not be the case; the date and time can have originated in another time zone with the same offset.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc6cc-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc6cc-160">See also</span></span>

- [<span data-ttu-id="cc6cc-161">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="cc6cc-161">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)

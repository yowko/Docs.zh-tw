---
title: "具現化 DateTimeOffset 物件"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f072aecf45aaaf9bd4aec845a698d6f12916fedb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="instantiating-a-datetimeoffset-object"></a><span data-ttu-id="18629-102">具現化 DateTimeOffset 物件</span><span class="sxs-lookup"><span data-stu-id="18629-102">Instantiating a DateTimeOffset object</span></span>

<span data-ttu-id="18629-103"><xref:System.DateTimeOffset>結構提供數種方式來建立新<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-103">The <xref:System.DateTimeOffset> structure offers a number of ways to create new <xref:System.DateTimeOffset> values.</span></span> <span data-ttu-id="18629-104">其中許多直接對應到可用的方法具現化新<xref:System.DateTime>與增強功能，可讓您指定的日期和時間值國際標準時間 (UTC) 位移的值。</span><span class="sxs-lookup"><span data-stu-id="18629-104">Many of them correspond directly to the methods available for instantiating new <xref:System.DateTime> values, with enhancements that allow you to specify the date and time value's offset from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="18629-105">特別是，您可以具現化<xref:System.DateTimeOffset>值如下：</span><span class="sxs-lookup"><span data-stu-id="18629-105">In particular, you can instantiate a <xref:System.DateTimeOffset> value in the following ways:</span></span>

* <span data-ttu-id="18629-106">使用日期和時間常值。</span><span class="sxs-lookup"><span data-stu-id="18629-106">By using a date and time literal.</span></span>

* <span data-ttu-id="18629-107">藉由呼叫<xref:System.DateTimeOffset>建構函式。</span><span class="sxs-lookup"><span data-stu-id="18629-107">By calling a <xref:System.DateTimeOffset> constructor.</span></span>

* <span data-ttu-id="18629-108">透過隱含地將值轉換為<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-108">By implicitly converting a value to <xref:System.DateTimeOffset> value.</span></span>

* <span data-ttu-id="18629-109">剖析日期和時間的字串表示。</span><span class="sxs-lookup"><span data-stu-id="18629-109">By parsing the string representation of a date and time.</span></span>

<span data-ttu-id="18629-110">本主題提供更詳細資料和程式碼範例以說明這些方法具現化新<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-110">This topic provides greater detail and code examples that illustrate these methods of instantiating new <xref:System.DateTimeOffset> values.</span></span>

## <a name="date-and-time-literals"></a><span data-ttu-id="18629-111">日期和時間常值</span><span class="sxs-lookup"><span data-stu-id="18629-111">Date and time literals</span></span>

<span data-ttu-id="18629-112">支援它，其中一種最常見的方式來具現化的語言<xref:System.DateTime>價值是提供的日期和時間做為硬式編碼的常值。</span><span class="sxs-lookup"><span data-stu-id="18629-112">For languages that support it, one of the most common ways to instantiate a <xref:System.DateTime> value is to provide the date and time as a hard-coded literal value.</span></span> <span data-ttu-id="18629-113">例如，下列 Visual Basic 程式碼會建立<xref:System.DateTime>物件，其值為 2008 年 1 月 1 日上午 10:00。</span><span class="sxs-lookup"><span data-stu-id="18629-113">For example, the following Visual Basic code creates a <xref:System.DateTime> object whose value is January 1, 2008, at 10:00 AM.</span></span>

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<span data-ttu-id="18629-114"><xref:System.DateTimeOffset>值也可以初始化使用支援的語言時，使用日期和時間常值<xref:System.DateTime>常值。</span><span class="sxs-lookup"><span data-stu-id="18629-114"><xref:System.DateTimeOffset> values can also be initialized using date and time literals when using languages that support <xref:System.DateTime> literals.</span></span> <span data-ttu-id="18629-115">例如，下列 Visual Basic 程式碼會建立<xref:System.DateTimeOffset>物件。</span><span class="sxs-lookup"><span data-stu-id="18629-115">For example, the following Visual Basic code creates a <xref:System.DateTimeOffset> object.</span></span>

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

<span data-ttu-id="18629-116">如主控台輸出所示，<xref:System.DateTimeOffset>以此方式建立的值會指派的當地時區位移。</span><span class="sxs-lookup"><span data-stu-id="18629-116">As the console output shows, the <xref:System.DateTimeOffset> value created in this way is assigned the offset of the local time zone.</span></span> <span data-ttu-id="18629-117">這表示<xref:System.DateTimeOffset>使用字元常值指派的值無法識別單一時間點執行程式碼在不同電腦上。</span><span class="sxs-lookup"><span data-stu-id="18629-117">This means that a <xref:System.DateTimeOffset> value assigned using a character literal does not identify a single point of time if the code is run on different computers.</span></span>

## <a name="datetimeoffset-constructors"></a><span data-ttu-id="18629-118">DateTimeOffset 建構函式</span><span class="sxs-lookup"><span data-stu-id="18629-118">DateTimeOffset constructors</span></span>

<span data-ttu-id="18629-119"><xref:System.DateTimeOffset>型別定義六個建構函式。</span><span class="sxs-lookup"><span data-stu-id="18629-119">The <xref:System.DateTimeOffset> type defines six constructors.</span></span> <span data-ttu-id="18629-120">其中四個直接對應<xref:System.DateTime>的建構函式，其他的型別參數<xref:System.TimeSpan>所定義的日期和時間的 UTC 位移。</span><span class="sxs-lookup"><span data-stu-id="18629-120">Four of them correspond directly to <xref:System.DateTime> constructors, with an additional parameter of type <xref:System.TimeSpan> that defines the date and time's offset from UTC.</span></span> <span data-ttu-id="18629-121">這些選項可讓您定義<xref:System.DateTimeOffset>值根據其個別的日期和時間元件的值。</span><span class="sxs-lookup"><span data-stu-id="18629-121">These allow you to define a <xref:System.DateTimeOffset> value based on the value of its individual date and time components.</span></span> <span data-ttu-id="18629-122">例如，下列程式碼會使用這些四個建構函式來具現化<xref:System.DateTimeOffset>物件相同的值，2008 年 7 月 1 日的上午 12:05 + 01:00。</span><span class="sxs-lookup"><span data-stu-id="18629-122">For example, the following code uses these four constructors to instantiate <xref:System.DateTimeOffset> objects with identical values of 7/1/2008 12:05 AM +01:00.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

<span data-ttu-id="18629-123">請注意，當值<xref:System.DateTimeOffset>使用具現化物件<xref:System.Globalization.PersianCalendar>主控台就會顯示為其建構函式的引數的其中一個物件，表示為西曆，而不是波斯曆中的日期。</span><span class="sxs-lookup"><span data-stu-id="18629-123">Note that, when the value of the <xref:System.DateTimeOffset> object instantiated using a <xref:System.Globalization.PersianCalendar> object as one of the arguments to its constructor is displayed to the console, it is expressed as a date in the Gregorian rather than the Persian calendar.</span></span> <span data-ttu-id="18629-124">若要輸出使用波斯曆中的日期，請參閱中的範例<xref:System.Globalization.PersianCalendar>主題。</span><span class="sxs-lookup"><span data-stu-id="18629-124">To output a date using the Persian calendar, see the example in the <xref:System.Globalization.PersianCalendar> topic.</span></span>

<span data-ttu-id="18629-125">其他兩個建構函式建立<xref:System.DateTimeOffset>物件從<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="18629-125">The other two constructors create a <xref:System.DateTimeOffset> object from a <xref:System.DateTime> value.</span></span> <span data-ttu-id="18629-126">第一個具有單一參數，<xref:System.DateTime>要轉換成值<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-126">The first of these has a single parameter, the <xref:System.DateTime> value to convert to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="18629-127">產生的位移<xref:System.DateTimeOffset>值取決於<xref:System.DateTime.Kind%2A>建構函式的單一參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="18629-127">The offset of the resulting <xref:System.DateTimeOffset> value depends on the <xref:System.DateTime.Kind%2A> property of the constructor's single parameter.</span></span> <span data-ttu-id="18629-128">如果其值為<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，位移設為等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="18629-128">If its value is <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, the offset is set equal to <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18629-129">否則，它的位移是設定為等於當地時區。</span><span class="sxs-lookup"><span data-stu-id="18629-129">Otherwise, its offset is set equal to that of the local time zone.</span></span> <span data-ttu-id="18629-130">下列範例說明如何使用這個建構函式來具現化<xref:System.DateTimeOffset>代表 UTC 與本地時區的物件：</span><span class="sxs-lookup"><span data-stu-id="18629-130">The following example illustrates the use of this constructor to instantiate <xref:System.DateTimeOffset> objects representing UTC and the local time zone:</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> <span data-ttu-id="18629-131">呼叫的多載<xref:System.DateTimeOffset>建構函式具有單一<xref:System.DateTime>參數相當於執行的隱含轉換<xref:System.DateTime>值設定為<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-131">Calling the overload of the <xref:System.DateTimeOffset> constructor that has a single <xref:System.DateTime> parameter is equivalent to performing an implicit conversion of a <xref:System.DateTime> value to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="18629-132">建立第二個建構函式<xref:System.DateTimeOffset>物件從<xref:System.DateTime>值有兩個參數：<xref:System.DateTime>轉換值，和<xref:System.TimeSpan>代表的日期和時間的值與 UTC 的時差。</span><span class="sxs-lookup"><span data-stu-id="18629-132">The second constructor that creates a <xref:System.DateTimeOffset> object from a <xref:System.DateTime> value has two parameters: the <xref:System.DateTime> value to convert, and a <xref:System.TimeSpan> value representing the date and time's offset from UTC.</span></span> <span data-ttu-id="18629-133">此位移的值必須對應到<xref:System.DateTime.Kind%2A>建構函式的第一個參數的屬性或<xref:System.ArgumentException>就會擲回。</span><span class="sxs-lookup"><span data-stu-id="18629-133">This offset value must correspond to the <xref:System.DateTime.Kind%2A> property of the constructor's first parameter or an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="18629-134">如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，第二個參數的值必須是<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="18629-134">If the <xref:System.DateTime.Kind%2A> property of the first parameter is <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, the value of the second parameter must be <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18629-135">如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Local?displayProperty=nameWithType>，第二個參數的值必須是本機系統時區位移。</span><span class="sxs-lookup"><span data-stu-id="18629-135">If the <xref:System.DateTime.Kind%2A> property of the first parameter is <xref:System.DateTimeKind.Local?displayProperty=nameWithType>, the value of the second parameter must be the offset of the local system's time zone.</span></span> <span data-ttu-id="18629-136">如果<xref:System.DateTime.Kind%2A>屬性的第一個參數是<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，位移可以是任何有效的值。</span><span class="sxs-lookup"><span data-stu-id="18629-136">If the <xref:System.DateTime.Kind%2A> property of the first parameter is <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, the offset can be any valid value.</span></span> <span data-ttu-id="18629-137">下列程式碼說明如何呼叫這個建構函式轉換<xref:System.DateTime>至<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-137">The following code illustrates calls to this constructor to convert <xref:System.DateTime> to <xref:System.DateTimeOffset> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a><span data-ttu-id="18629-138">隱含類型轉換</span><span class="sxs-lookup"><span data-stu-id="18629-138">Implicit type conversion</span></span>

<span data-ttu-id="18629-139"><xref:System.DateTimeOffset>類型支援一個隱含類型轉換： 從<xref:System.DateTime>值設定為<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-139">The <xref:System.DateTimeOffset> type supports one implicit type conversion: from a <xref:System.DateTime> value to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="18629-140">隱含類型轉換是從某種類型到另一種類型的轉換，這不需要明確轉型 (在 C# 中) 或轉換 (在 Visual Basic 中)，而且不會遺失資訊。</span><span class="sxs-lookup"><span data-stu-id="18629-140">(An implicit type conversion is a conversion from one type to another that does not require an explicit cast (in C#) or conversion (in Visual Basic) and that does not lose information.</span></span> <span data-ttu-id="18629-141">這樣就可以使用如下所述的程式碼。</span><span class="sxs-lookup"><span data-stu-id="18629-141">It makes code like the following possible.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

<span data-ttu-id="18629-142">產生的位移<xref:System.DateTimeOffset>值取決於<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>屬性值。</span><span class="sxs-lookup"><span data-stu-id="18629-142">The offset of the resulting <xref:System.DateTimeOffset> value depends on the <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> property value.</span></span> <span data-ttu-id="18629-143">如果其值為<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>，位移設為等於<xref:System.TimeSpan.Zero?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="18629-143">If its value is <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>, the offset is set equal to <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18629-144">如果其值為 <xref:System.DateTimeKind.Local?displayProperty=nameWithType>或<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>，位移設為等於當地時區。</span><span class="sxs-lookup"><span data-stu-id="18629-144">If its value is either <xref:System.DateTimeKind.Local?displayProperty=nameWithType> or <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, the offset is set equal to that of the local time zone.</span></span>

## <a name="parsing-the-string-representation-of-a-date-and-time"></a><span data-ttu-id="18629-145">剖析日期和時間的字串的表示</span><span class="sxs-lookup"><span data-stu-id="18629-145">Parsing the string representation of a date and time</span></span>

<span data-ttu-id="18629-146"><xref:System.DateTimeOffset>型別支援四種方法可讓您將日期的字串表示轉換成時間<xref:System.DateTimeOffset>值：</span><span class="sxs-lookup"><span data-stu-id="18629-146">The <xref:System.DateTimeOffset> type supports four methods that allow you to convert the string representation of a date and time into a <xref:System.DateTimeOffset> value:</span></span>

* <span data-ttu-id="18629-147"><xref:System.DateTimeOffset.Parse%2A>它會嘗試轉換的字串表示日期和時間<xref:System.DateTimeOffset>值，並擲回例外狀況，如果轉換失敗。</span><span class="sxs-lookup"><span data-stu-id="18629-147"><xref:System.DateTimeOffset.Parse%2A>, which tries to convert the string representation of a date and time to a <xref:System.DateTimeOffset> value and throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="18629-148"><xref:System.DateTimeOffset.TryParse%2A>它會嘗試轉換的字串表示日期和時間<xref:System.DateTimeOffset>值並傳回`false`如果轉換失敗。</span><span class="sxs-lookup"><span data-stu-id="18629-148"><xref:System.DateTimeOffset.TryParse%2A>, which tries to convert the string representation of a date and time to a <xref:System.DateTimeOffset> value and returns `false` if the conversion fails.</span></span>

* <span data-ttu-id="18629-149"><xref:System.DateTimeOffset.ParseExact%2A>其中嘗試的日期和時間，以指定格式的字串表示轉換成<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-149"><xref:System.DateTimeOffset.ParseExact%2A>, which tries to convert the string representation of a date and time in a specified format to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="18629-150">方法會在轉換失敗時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="18629-150">The method throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="18629-151"><xref:System.DateTimeOffset.TryParseExact%2A>其中嘗試的日期和時間，以指定格式的字串表示轉換成<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-151"><xref:System.DateTimeOffset.TryParseExact%2A>, which tries to convert the string representation of a date and time in a specified format to a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="18629-152">如果轉換失敗，方法會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="18629-152">The method returns `false` if the conversion fails.</span></span>

<span data-ttu-id="18629-153">下列範例說明如何具現化每個四個字串轉換方法呼叫<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="18629-153">The following example illustrates calls to each of these four string conversion methods to instantiate a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a><span data-ttu-id="18629-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="18629-154">See also</span></span>

[<span data-ttu-id="18629-155">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="18629-155">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)

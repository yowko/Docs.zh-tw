---
title: "如何：反覆存取日期和時間值"
ms.custom: 
ms.date: 03/30/2017
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
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="92294-102">如何：反覆存取日期和時間值</span><span class="sxs-lookup"><span data-stu-id="92294-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="92294-103">在許多應用程式中，日期和時間值的用途都是要明確地識別單一時間點。</span><span class="sxs-lookup"><span data-stu-id="92294-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="92294-104">本主題說明如何儲存和還原<xref:System.DateTime>值<xref:System.DateTimeOffset>值和時間的日期和時間值區域資訊，以便還原的值識別儲存的值在同時間。</span><span class="sxs-lookup"><span data-stu-id="92294-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="92294-105">若要反覆存取 DateTime 值</span><span class="sxs-lookup"><span data-stu-id="92294-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="92294-106">轉換<xref:System.DateTime>值至它的字串表示，藉由呼叫<xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>使用"o"格式規範的方法。</span><span class="sxs-lookup"><span data-stu-id="92294-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="92294-107">儲存的字串表示<xref:System.DateTime>值至檔案，或跨處理序、 應用程式網域或電腦界限傳遞它。</span><span class="sxs-lookup"><span data-stu-id="92294-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="92294-108">擷取字串，代表<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="92294-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="92294-109">呼叫<xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>方法，然後傳遞<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>做為值`styles`參數。</span><span class="sxs-lookup"><span data-stu-id="92294-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="92294-110">下列範例說明如何來回<xref:System.DateTime>值。</span><span class="sxs-lookup"><span data-stu-id="92294-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="92294-111">當往返<xref:System.DateTime>值，這項技術成功會保留所有本機和國際時間的時間。</span><span class="sxs-lookup"><span data-stu-id="92294-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="92294-112">例如，如果本機<xref:System.DateTime>在美國太平洋時區系統上儲存值太平洋標準時區的系統上，但該值在美國中央標準時區的系統上還原，則還原的日期和時間會比原始時間晚兩個小時，以反映出兩個時區之間的時間差異。</span><span class="sxs-lookup"><span data-stu-id="92294-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="92294-113">不過，針對未指定的時間，這項技術並不一定準確。</span><span class="sxs-lookup"><span data-stu-id="92294-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="92294-114">所有<xref:System.DateTime>值其<xref:System.DateTime.Kind%2A>屬性是<xref:System.DateTimeKind.Unspecified>會視為它們都是當地時間。</span><span class="sxs-lookup"><span data-stu-id="92294-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="92294-115">如果這不是如此，<xref:System.DateTime>不就會成功地識別正確的點的時間。</span><span class="sxs-lookup"><span data-stu-id="92294-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="92294-116">這項限制的因應措施，是將日期和時間值與其儲存和還原作業的時區緊密結合。</span><span class="sxs-lookup"><span data-stu-id="92294-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="92294-117">若要反覆存取 DateTimeOffset 值</span><span class="sxs-lookup"><span data-stu-id="92294-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="92294-118">轉換<xref:System.DateTimeOffset>值至它的字串表示，藉由呼叫<xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>使用"o"格式規範的方法。</span><span class="sxs-lookup"><span data-stu-id="92294-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="92294-119">儲存的字串表示<xref:System.DateTimeOffset>值至檔案，或跨處理序、 應用程式網域或電腦界限傳遞它。</span><span class="sxs-lookup"><span data-stu-id="92294-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="92294-120">擷取字串，代表<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="92294-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="92294-121">呼叫<xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType>方法，然後傳遞<xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>做為值`styles`參數。</span><span class="sxs-lookup"><span data-stu-id="92294-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="92294-122">下列範例說明如何來回<xref:System.DateTimeOffset>值。</span><span class="sxs-lookup"><span data-stu-id="92294-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="92294-123">這項技術一律明確地識別<xref:System.DateTimeOffset>為單一時間點的值。</span><span class="sxs-lookup"><span data-stu-id="92294-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="92294-124">值可以再轉換為國際標準時間 (UTC) 藉由呼叫<xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType>方法，或它可以轉換為特定時區的時間呼叫<xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType>或<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="92294-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="92294-125">這項技術的主要限制是該日期和時間執行算術、<xref:System.DateTimeOffset>值，表示為特定時區的時間可能不會產生精確的結果，該時區。</span><span class="sxs-lookup"><span data-stu-id="92294-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="92294-126">這是因為當<xref:System.DateTimeOffset>產生值時，它會與其時區解除關聯。</span><span class="sxs-lookup"><span data-stu-id="92294-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="92294-127">因此，當您執行日期和時間計算時，就無法再套用該時區的調整規則。</span><span class="sxs-lookup"><span data-stu-id="92294-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="92294-128">若要解決這個問題，您可以定義自訂類型，以包含日期與時間值及其隨附的時區。</span><span class="sxs-lookup"><span data-stu-id="92294-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="92294-129">反覆存取日期和時間值具有時區</span><span class="sxs-lookup"><span data-stu-id="92294-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="92294-130">定義類別或結構包含兩個欄位。</span><span class="sxs-lookup"><span data-stu-id="92294-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="92294-131">第一個欄位是<xref:System.DateTime>或<xref:System.DateTimeOffset>物件，而第二個是<xref:System.TimeZoneInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="92294-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="92294-132">下列範例是這類類型的簡單版本。</span><span class="sxs-lookup"><span data-stu-id="92294-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="92294-133">將此類別標示與<xref:System.SerializableAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="92294-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="92294-134">序列化物件使用<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="92294-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="92294-135">物件使用還原<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="92294-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="92294-136">轉型 （C# 中） 或者 （在 Visual Basic) 已還原序列化的物件轉換成適當型別的物件。</span><span class="sxs-lookup"><span data-stu-id="92294-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="92294-137">下列範例說明如何反覆存取的物件會儲存日期和時間以及時區資訊。</span><span class="sxs-lookup"><span data-stu-id="92294-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="92294-138">這項技術應該一律明確地反映正確的時間兩者之前和之後儲存和還原，結合的日期和時間以及時區物件的實作不允許的日期值，成為與同步處理點時區值。</span><span class="sxs-lookup"><span data-stu-id="92294-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="92294-139">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="92294-139">Compiling the Code</span></span>  
 <span data-ttu-id="92294-140">這些範例需要：</span><span class="sxs-lookup"><span data-stu-id="92294-140">These examples require:</span></span>  
  
-   <span data-ttu-id="92294-141">使用 C# 匯入下列命名空間`using`陳述式或[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]`Imports`陳述式：</span><span class="sxs-lookup"><span data-stu-id="92294-141">That the following namespaces be imported with C# `using` statements or [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="92294-142"><xref:System>（僅限 C#)。</span><span class="sxs-lookup"><span data-stu-id="92294-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="92294-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92294-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="92294-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92294-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="92294-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92294-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="92294-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="92294-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="92294-147">對 System.Core.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="92294-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="92294-148">每個程式碼範例中，除了`DateInTimeZone`類別，應該包含在類別或 Visual Basic 的 module，包裝在方法中，並從呼叫`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="92294-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92294-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92294-149">See Also</span></span>  
 [<span data-ttu-id="92294-150">執行格式化作業</span><span class="sxs-lookup"><span data-stu-id="92294-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="92294-151">在 DateTime、DateTimeOffset、TimeSpan 和 TimeZoneInfo 之間選擇</span><span class="sxs-lookup"><span data-stu-id="92294-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="92294-152">Standard Date and Time Format Strings</span><span class="sxs-lookup"><span data-stu-id="92294-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)

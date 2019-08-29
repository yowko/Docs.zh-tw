---
title: 儲存和還原時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea44b29eaa0273baadbf02093108bc4da912a3e5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106736"
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="43122-102">儲存和還原時區</span><span class="sxs-lookup"><span data-stu-id="43122-102">Saving and restoring time zones</span></span>

<span data-ttu-id="43122-103"><xref:System.TimeZoneInfo>類別依賴登錄來取出預先定義的時區資料。</span><span class="sxs-lookup"><span data-stu-id="43122-103">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="43122-104">不過, 登錄是動態結構。</span><span class="sxs-lookup"><span data-stu-id="43122-104">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="43122-105">此外, 作業系統會使用登錄所包含的時區資訊, 主要用來處理目前年份的時間調整和轉換。</span><span class="sxs-lookup"><span data-stu-id="43122-105">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="43122-106">這對於依賴正確時區資料的應用程式有兩個主要的含意:</span><span class="sxs-lookup"><span data-stu-id="43122-106">This has two major implications for applications that rely on accurate time zone data:</span></span>

- <span data-ttu-id="43122-107">應用程式所需的時區可能未定義于登錄中, 或可能已從登錄中重新命名或移除。</span><span class="sxs-lookup"><span data-stu-id="43122-107">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

- <span data-ttu-id="43122-108">在登錄中定義的時區可能缺少歷程記錄時區轉換所需之特定調整規則的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="43122-108">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="43122-109"><xref:System.TimeZoneInfo>類別透過支援序列化 (儲存) 和還原序列化 (還原) 時區資料, 來解決這些限制。</span><span class="sxs-lookup"><span data-stu-id="43122-109">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="43122-110">時區序列化和還原序列化</span><span class="sxs-lookup"><span data-stu-id="43122-110">Time zone serialization and deserialization</span></span>

<span data-ttu-id="43122-111">藉由序列化和還原序列化時區資料來儲存和還原時區, 只需要兩個方法呼叫:</span><span class="sxs-lookup"><span data-stu-id="43122-111">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

- <span data-ttu-id="43122-112">您可以藉由<xref:System.TimeZoneInfo>呼叫該物件的<xref:System.TimeZoneInfo.ToSerializedString%2A>方法來序列化物件。</span><span class="sxs-lookup"><span data-stu-id="43122-112">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="43122-113">方法不接受任何參數, 而且會傳回包含時區資訊的字串。</span><span class="sxs-lookup"><span data-stu-id="43122-113">The method takes no parameters and returns a string that contains time zone information.</span></span>

- <span data-ttu-id="43122-114">您可以<xref:System.TimeZoneInfo>藉由將該字串傳遞`static`至 (`Shared`在 Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>方法中, 將物件從序列化的字串還原序列化。</span><span class="sxs-lookup"><span data-stu-id="43122-114">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="43122-115">序列化和還原序列化案例</span><span class="sxs-lookup"><span data-stu-id="43122-115">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="43122-116">能夠將<xref:System.TimeZoneInfo>物件儲存 (或序列化) 至字串, 並還原 (或還原序列化) 它以供稍後使用, 同時增加了公用程式和<xref:System.TimeZoneInfo>類別的彈性。</span><span class="sxs-lookup"><span data-stu-id="43122-116">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="43122-117">本節將探討序列化和還原序列化最有用的一些情況。</span><span class="sxs-lookup"><span data-stu-id="43122-117">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="43122-118">序列化和還原序列化應用程式中的時區資料</span><span class="sxs-lookup"><span data-stu-id="43122-118">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="43122-119">您可以視需要從字串還原序列化的時區。</span><span class="sxs-lookup"><span data-stu-id="43122-119">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="43122-120">如果從登錄中抓取的時區無法正確轉換特定日期範圍內的日期和時間, 應用程式可能會這麼做。</span><span class="sxs-lookup"><span data-stu-id="43122-120">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="43122-121">例如, Windows XP 登錄中的時區資料支援單一調整規則, 而 Windows Vista 登錄中所定義的時間區域通常會提供兩個調整規則的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="43122-121">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="43122-122">這表示歷程記錄時間轉換可能不正確。</span><span class="sxs-lookup"><span data-stu-id="43122-122">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="43122-123">時區資料的序列化和還原序列化可以處理這項限制。</span><span class="sxs-lookup"><span data-stu-id="43122-123">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="43122-124">在下列範例中, 未定義<xref:System.TimeZoneInfo>任何調整規則的自訂類別, 以代表美國美國東部標準時區 (從1883到 1917), 在日光節約時間推出之前。</span><span class="sxs-lookup"><span data-stu-id="43122-124">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="43122-125">自訂時區會在具有全域範圍的變數中序列化。</span><span class="sxs-lookup"><span data-stu-id="43122-125">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="43122-126">時區轉換方法`ConvertUtcTime`會傳遞國際標準時間 (UTC) 時間來進行轉換。</span><span class="sxs-lookup"><span data-stu-id="43122-126">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="43122-127">如果日期和時間發生在1917或更早的版本中, 自訂的東部標準時區會從序列化字串還原, 並取代從登錄中抓取的時區。</span><span class="sxs-lookup"><span data-stu-id="43122-127">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="43122-128">處理時區例外狀況</span><span class="sxs-lookup"><span data-stu-id="43122-128">Handling time zone exceptions</span></span>

<span data-ttu-id="43122-129">由於登錄是動態結構, 因此其內容會受到意外或刻意的修改。</span><span class="sxs-lookup"><span data-stu-id="43122-129">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="43122-130">這表示應該在登錄中定義且應用程式成功執行所需的時區不存在。</span><span class="sxs-lookup"><span data-stu-id="43122-130">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="43122-131">不支援時區序列化和還原序列化, 您只需要進行一些選擇, 但要處理<xref:System.TimeZoneNotFoundException>藉由結束應用程式所產生的。</span><span class="sxs-lookup"><span data-stu-id="43122-131">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="43122-132">不過, 藉由使用時區序列化和還原序列化, 您可以藉由<xref:System.TimeZoneNotFoundException>從序列化字串還原所需的時區來處理非預期的, 應用程式將會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="43122-132">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="43122-133">下列範例會建立並序列化自訂的中央標準時區。</span><span class="sxs-lookup"><span data-stu-id="43122-133">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="43122-134">然後, 它會嘗試從登錄中取出中央標準時區。</span><span class="sxs-lookup"><span data-stu-id="43122-134">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="43122-135">如果抓取作業擲回<xref:System.TimeZoneNotFoundException> <xref:System.InvalidTimeZoneException>或, 則例外狀況處理常式會將時區還原序列化。</span><span class="sxs-lookup"><span data-stu-id="43122-135">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="43122-136">儲存序列化字串, 並在需要時進行還原</span><span class="sxs-lookup"><span data-stu-id="43122-136">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="43122-137">先前的範例將時區資訊儲存至字串變數, 並在需要時加以還原。</span><span class="sxs-lookup"><span data-stu-id="43122-137">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="43122-138">不過, 包含序列化時區資訊的字串本身可以儲存在某些儲存媒體中, 例如外部檔案、內嵌在應用程式中的資源檔, 或登錄。</span><span class="sxs-lookup"><span data-stu-id="43122-138">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="43122-139">(請注意, 自訂時區的相關資訊應該與登錄中系統的時區金鑰分開儲存)。</span><span class="sxs-lookup"><span data-stu-id="43122-139">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="43122-140">以此方式儲存序列化的時區字串也會將時區建立常式與應用程式本身分開。</span><span class="sxs-lookup"><span data-stu-id="43122-140">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="43122-141">例如, 時區建立常式可以執行並建立資料檔, 其中包含應用程式可使用的歷程記錄時區資訊。</span><span class="sxs-lookup"><span data-stu-id="43122-141">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="43122-142">然後, 您可以在應用程式中安裝資料檔案, 並且可以開啟它, 並在應用程式需要時, 將它的一個或多個時區還原序列化。</span><span class="sxs-lookup"><span data-stu-id="43122-142">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="43122-143">如需使用內嵌資源來儲存序列化的時區資料的範例, 請參閱[如何:將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) , 以及[如何:從內嵌資源](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)還原時區。</span><span class="sxs-lookup"><span data-stu-id="43122-143">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="43122-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43122-144">See also</span></span>

- [<span data-ttu-id="43122-145">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="43122-145">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)

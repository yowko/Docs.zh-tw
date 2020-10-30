---
title: 儲存和還原時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET], time zones
- serialization [.NET], time zones
- time zone objects [.NET], restoring
- saving time zones
- time zone objects [.NET], deserializing
- time zones [.NET], saving
- time zones [.NET], restoring
- time zone objects [.NET], serializing
- time zone objects [.NET], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
ms.openlocfilehash: 6a05bf4ce062a3f4e539e9b89779cb468b9782a6
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063387"
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="53920-102">儲存和還原時區</span><span class="sxs-lookup"><span data-stu-id="53920-102">Saving and restoring time zones</span></span>

<span data-ttu-id="53920-103"><xref:System.TimeZoneInfo>類別會依賴登錄來取得預先定義的時區資料。</span><span class="sxs-lookup"><span data-stu-id="53920-103">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="53920-104">但是，登錄是動態結構。</span><span class="sxs-lookup"><span data-stu-id="53920-104">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="53920-105">此外，作業系統會使用登錄所包含的時區資訊，主要是用來處理目前年度的時間調整和轉換。</span><span class="sxs-lookup"><span data-stu-id="53920-105">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="53920-106">對於依賴精確時區資料的應用程式，這有兩個主要的含意：</span><span class="sxs-lookup"><span data-stu-id="53920-106">This has two major implications for applications that rely on accurate time zone data:</span></span>

- <span data-ttu-id="53920-107">應用程式所需的時區可能不會定義于登錄中，也可能已重新命名或從登錄中移除。</span><span class="sxs-lookup"><span data-stu-id="53920-107">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

- <span data-ttu-id="53920-108">在登錄中定義的時區可能缺少歷程記錄時區轉換所需之特定調整規則的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="53920-108">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="53920-109"><xref:System.TimeZoneInfo>類別透過其序列化支援來解決這些限制 (儲存) 和還原序列化 (還原時區資料) 。</span><span class="sxs-lookup"><span data-stu-id="53920-109">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="53920-110">時區序列化和還原序列化</span><span class="sxs-lookup"><span data-stu-id="53920-110">Time zone serialization and deserialization</span></span>

<span data-ttu-id="53920-111">藉由將時區資料序列化和還原序列化來儲存和還原時區，只需要兩個方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="53920-111">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

- <span data-ttu-id="53920-112">您可以藉 <xref:System.TimeZoneInfo> 由呼叫物件的方法來序列化物件 <xref:System.TimeZoneInfo.ToSerializedString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="53920-112">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="53920-113">方法不接受任何參數，而且會傳回包含時區資訊的字串。</span><span class="sxs-lookup"><span data-stu-id="53920-113">The method takes no parameters and returns a string that contains time zone information.</span></span>

- <span data-ttu-id="53920-114">您可以將 <xref:System.TimeZoneInfo> 該字串傳遞至 `static` `Shared` Visual Basic) 方法中的 (，以從序列化字串還原序列化物件 <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="53920-114">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="53920-115">序列化和還原序列化案例</span><span class="sxs-lookup"><span data-stu-id="53920-115">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="53920-116">可以儲存 (或將物件序列化) <xref:System.TimeZoneInfo> 至字串，以及還原 (或還原序列化) 以供稍後使用，以同時提高類別的公用程式和彈性 <xref:System.TimeZoneInfo> 。</span><span class="sxs-lookup"><span data-stu-id="53920-116">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="53920-117">本節將探討序列化和還原序列化最有用的部分情況。</span><span class="sxs-lookup"><span data-stu-id="53920-117">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="53920-118">序列化和還原序列化應用程式中的時區資料</span><span class="sxs-lookup"><span data-stu-id="53920-118">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="53920-119">您可以視需要從字串還原序列化的時區。</span><span class="sxs-lookup"><span data-stu-id="53920-119">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="53920-120">如果從登錄取出的時區無法正確轉換特定日期範圍內的日期和時間，應用程式可能會這樣做。</span><span class="sxs-lookup"><span data-stu-id="53920-120">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="53920-121">例如，Windows XP 登錄區中的時區資料支援單一調整規則，而 Windows Vista 登錄中定義的時區通常會提供兩個調整規則的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="53920-121">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="53920-122">這表示歷程記錄時間轉換可能不正確。</span><span class="sxs-lookup"><span data-stu-id="53920-122">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="53920-123">時區資料的序列化和還原序列化可以處理這項限制。</span><span class="sxs-lookup"><span data-stu-id="53920-123">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="53920-124">在下列範例中，所定義的自訂 <xref:System.TimeZoneInfo> 類別沒有調整規則，該類別代表從 1883 到 1917 年，日光節約時間推行之前的美國東部標準時間時區。</span><span class="sxs-lookup"><span data-stu-id="53920-124">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="53920-125">自訂時區會在具有全域範圍的變數中序列化。</span><span class="sxs-lookup"><span data-stu-id="53920-125">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="53920-126">時區轉換方法 `ConvertUtcTime` 會傳遞國際標準時間 (UTC) 次轉換。</span><span class="sxs-lookup"><span data-stu-id="53920-126">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="53920-127">如果日期和時間發生在1917或更早版本中，自訂的東部標準時區會從序列化字串還原，並取代從登錄取出的時區。</span><span class="sxs-lookup"><span data-stu-id="53920-127">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="53920-128">處理時區例外狀況</span><span class="sxs-lookup"><span data-stu-id="53920-128">Handling time zone exceptions</span></span>

<span data-ttu-id="53920-129">由於登錄是動態結構，因此其內容可能會遭到意外或刻意修改。</span><span class="sxs-lookup"><span data-stu-id="53920-129">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="53920-130">這表示應該在登錄中定義，而且應用程式順利執行所需的時區可能不存在。</span><span class="sxs-lookup"><span data-stu-id="53920-130">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="53920-131">如果不支援時區序列化和還原序列化，您就不需要進行任何選擇，而是藉 <xref:System.TimeZoneNotFoundException> 由結束應用程式來處理結果。</span><span class="sxs-lookup"><span data-stu-id="53920-131">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="53920-132">不過，藉由使用時區序列化和還原序列化，您可以 <xref:System.TimeZoneNotFoundException> 從序列化字串還原所需的時區，以處理非預期的，應用程式將會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="53920-132">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="53920-133">下列範例會建立並序列化自訂中央標準時區。</span><span class="sxs-lookup"><span data-stu-id="53920-133">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="53920-134">然後，它會嘗試從登錄中取出中央標準時區。</span><span class="sxs-lookup"><span data-stu-id="53920-134">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="53920-135">如果抓取作業擲回 <xref:System.TimeZoneNotFoundException> 或 <xref:System.InvalidTimeZoneException> ，則例外狀況處理常式會將時區還原序列化。</span><span class="sxs-lookup"><span data-stu-id="53920-135">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="53920-136">儲存序列化字串並在需要時還原</span><span class="sxs-lookup"><span data-stu-id="53920-136">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="53920-137">先前的範例將時區資訊儲存至字串變數，並在需要時加以還原。</span><span class="sxs-lookup"><span data-stu-id="53920-137">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="53920-138">不過，包含序列化時區資訊的字串本身可以儲存在某些儲存媒體中，例如外部檔案、內嵌于應用程式中的資源檔或登錄。</span><span class="sxs-lookup"><span data-stu-id="53920-138">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="53920-139"> (請注意，自訂時區的相關資訊應該與登錄中系統的時區金鑰分開儲存。 ) </span><span class="sxs-lookup"><span data-stu-id="53920-139">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="53920-140">以這種方式儲存序列化的時區字串也會將時區建立常式與應用程式本身分開。</span><span class="sxs-lookup"><span data-stu-id="53920-140">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="53920-141">例如，時區建立常式可以執行和建立資料檔，其中包含應用程式可使用的歷史時區資訊。</span><span class="sxs-lookup"><span data-stu-id="53920-141">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="53920-142">然後，您可以使用應用程式來安裝資料檔案，而且可以在應用程式需要時加以開啟，並且可以將它的一個或多個時區還原序列化。</span><span class="sxs-lookup"><span data-stu-id="53920-142">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="53920-143">如需使用內嵌資源儲存序列化時區資料的範例，請參閱 [如何：將時區儲存到內嵌資源](save-time-zones-to-an-embedded-resource.md) 和 [如何：從內嵌資源還原時區](restore-time-zones-from-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="53920-143">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53920-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53920-144">See also</span></span>

- [<span data-ttu-id="53920-145">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="53920-145">Dates, times, and time zones</span></span>](index.md)

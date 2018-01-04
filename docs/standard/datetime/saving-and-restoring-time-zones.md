---
title: "儲存和還原時區"
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9451b1b0ff41f32c31ef3574b5684ae5a02e252
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="saving-and-restoring-time-zones"></a><span data-ttu-id="0936a-102">儲存和還原時區</span><span class="sxs-lookup"><span data-stu-id="0936a-102">Saving and restoring time zones</span></span>

<span data-ttu-id="0936a-103"><xref:System.TimeZoneInfo>類別依賴登錄，以擷取預先定義的時區資料。</span><span class="sxs-lookup"><span data-stu-id="0936a-103">The <xref:System.TimeZoneInfo> class relies on the registry to retrieve predefined time zone data.</span></span> <span data-ttu-id="0936a-104">不過，登錄是動態的結構。</span><span class="sxs-lookup"><span data-stu-id="0936a-104">However, the registry is a dynamic structure.</span></span> <span data-ttu-id="0936a-105">此外，登錄包含時區資訊會由作業系統主要用來處理時間調整並轉換為目前的年份。</span><span class="sxs-lookup"><span data-stu-id="0936a-105">Additionally, the time zone information that the registry contains is used by the operating system primarily to handle time adjustments and conversions for the current year.</span></span> <span data-ttu-id="0936a-106">這有兩個主要的含意，依賴精確的時區資料的應用程式：</span><span class="sxs-lookup"><span data-stu-id="0936a-106">This has two major implications for applications that rely on accurate time zone data:</span></span>

* <span data-ttu-id="0936a-107">不可定義為應用程式所需的時區，在登錄中，或已重新命名或從登錄中移除。</span><span class="sxs-lookup"><span data-stu-id="0936a-107">A time zone that is required by an application may not be defined in the registry, or it may have been renamed or removed from the registry.</span></span>

* <span data-ttu-id="0936a-108">在登錄中定義的時區可能缺少所需的歷程記錄的時區轉換的特定的調整規則的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0936a-108">A time zone that is defined in the registry may lack information about the particular adjustment rules that are necessary for historical time zone conversions.</span></span>

<span data-ttu-id="0936a-109"><xref:System.TimeZoneInfo>類別會處理這些限制透過其支援的序列化 （儲存） 和還原序列化 （還原） 的時區資料。</span><span class="sxs-lookup"><span data-stu-id="0936a-109">The <xref:System.TimeZoneInfo> class addresses these limitations through its support for serialization (saving) and deserialization (restoring) of time zone data.</span></span>

## <a name="time-zone-serialization-and-deserialization"></a><span data-ttu-id="0936a-110">時區序列化和還原序列化</span><span class="sxs-lookup"><span data-stu-id="0936a-110">Time zone serialization and deserialization</span></span>

<span data-ttu-id="0936a-111">儲存和還原時區序列化和還原序列化的時區資料所牽涉到兩個方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="0936a-111">Saving and restoring a time zone by serializing and deserializing time zone data involves just two method calls:</span></span>

* <span data-ttu-id="0936a-112">您可以將序列化<xref:System.TimeZoneInfo>藉由呼叫該物件的物件<xref:System.TimeZoneInfo.ToSerializedString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0936a-112">You can serialize a <xref:System.TimeZoneInfo> object by calling that object's <xref:System.TimeZoneInfo.ToSerializedString%2A> method.</span></span> <span data-ttu-id="0936a-113">方法會採用任何參數，並傳回字串，包含時區資訊。</span><span class="sxs-lookup"><span data-stu-id="0936a-113">The method takes no parameters and returns a string that contains time zone information.</span></span>

* <span data-ttu-id="0936a-114">您可以還原序列化<xref:System.TimeZoneInfo>物件從已序列化的字串傳遞至該字串`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="0936a-114">You can deserialize a <xref:System.TimeZoneInfo> object from a serialized string by passing that string to the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> method.</span></span>

## <a name="serialization-and-deserialization-scenarios"></a><span data-ttu-id="0936a-115">序列化和還原序列化的案例</span><span class="sxs-lookup"><span data-stu-id="0936a-115">Serialization and deserialization scenarios</span></span>

<span data-ttu-id="0936a-116">儲存 （或序列化） 的能力<xref:System.TimeZoneInfo>物件的字串和要還原 （或還原序列化） 它以供稍後使用增加的彈性和公用程式<xref:System.TimeZoneInfo>類別。</span><span class="sxs-lookup"><span data-stu-id="0936a-116">The ability to save (or serialize) a <xref:System.TimeZoneInfo> object to a string and to restore (or deserialize) it for later use increases both the utility and the flexibility of the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="0936a-117">本節將說明部分的序列化和還原序列化是最有用的狀況。</span><span class="sxs-lookup"><span data-stu-id="0936a-117">This section examines some of the situations in which serialization and deserialization are most useful.</span></span>

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a><span data-ttu-id="0936a-118">序列化和還原序列化應用程式中的時區資料</span><span class="sxs-lookup"><span data-stu-id="0936a-118">Serializing and deserializing time zone data in an application</span></span>

<span data-ttu-id="0936a-119">在需要時，可以從字串還原序列化的時區。</span><span class="sxs-lookup"><span data-stu-id="0936a-119">A serialized time zone can be restored from a string when it is needed.</span></span> <span data-ttu-id="0936a-120">如果從登錄擷取時區是無法正確轉換的日期和時間的特定日期範圍內，應用程式可能此作業。</span><span class="sxs-lookup"><span data-stu-id="0936a-120">An application might do this if the time zone retrieved from the registry is unable to correctly convert a date and time within a particular date range.</span></span> <span data-ttu-id="0936a-121">雖然通常是在 Windows Vista 登錄中定義的時區資訊提供兩種調整規則，例如，Windows XP 登錄中的時區資料支援單一的調整規則。</span><span class="sxs-lookup"><span data-stu-id="0936a-121">For example, time zone data in the Windows XP registry supports a single adjustment rule, while time zones defined in the Windows Vista registry typically provide information about two adjustment rules.</span></span> <span data-ttu-id="0936a-122">這表示歷程記錄的時間轉換可能不正確。</span><span class="sxs-lookup"><span data-stu-id="0936a-122">This means that historical time conversions may be inaccurate.</span></span> <span data-ttu-id="0936a-123">序列化和還原序列化的時區資料可以處理這項限制。</span><span class="sxs-lookup"><span data-stu-id="0936a-123">Serialization and deserialization of time zone data can handle this limitation.</span></span>

<span data-ttu-id="0936a-124">在下列範例中，自訂<xref:System.TimeZoneInfo>沒有調整規則的類別定義來代表美國美加東部標準時間區域從 1883年 1917 之前在美國境內的日光節約時間的簡介。</span><span class="sxs-lookup"><span data-stu-id="0936a-124">In the following example, a custom <xref:System.TimeZoneInfo> class that has no adjustment rules is defined to represent the U.S. Eastern Standard Time zone from 1883 to 1917, before the introduction of daylight saving time in the United States.</span></span> <span data-ttu-id="0936a-125">自訂的時區會序列化具有全域範圍的變數中。</span><span class="sxs-lookup"><span data-stu-id="0936a-125">The custom time zone is serialized in a variable that has global scope.</span></span> <span data-ttu-id="0936a-126">時區轉換方法， `ConvertUtcTime`，傳遞至轉換 Coordinated Universal Time (UTC) 時間。</span><span class="sxs-lookup"><span data-stu-id="0936a-126">The time zone conversion method, `ConvertUtcTime`, is passed Coordinated Universal Time (UTC) times to convert.</span></span> <span data-ttu-id="0936a-127">如果日期和時間發生在 1917 年或更早版本，自訂美加東部標準時間區域還原序列化字串，並取代從登錄擷取時區。</span><span class="sxs-lookup"><span data-stu-id="0936a-127">If the date and time occurs in 1917 or earlier, the custom Eastern Standard Time zone is restored from a serialized string and replaces the time zone retrieved from the registry.</span></span>

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a><span data-ttu-id="0936a-128">時區例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="0936a-128">Handling time zone exceptions</span></span>

<span data-ttu-id="0936a-129">由於登錄是動態的結構，其內容可能會有所意外或蓄意修改。</span><span class="sxs-lookup"><span data-stu-id="0936a-129">Because the registry is a dynamic structure, its contents are subject to accidental or deliberate modification.</span></span> <span data-ttu-id="0936a-130">這表示時區，應該定義在登錄中，且成功執行應用程式需要可能不存在。</span><span class="sxs-lookup"><span data-stu-id="0936a-130">This means that a time zone that should be defined in the registry and that is required for an application to execute successfully may be absent.</span></span> <span data-ttu-id="0936a-131">沒有時區序列化和還原序列化的支援，您有很少的選擇，但若要處理產生<xref:System.TimeZoneNotFoundException>藉由結束應用程式。</span><span class="sxs-lookup"><span data-stu-id="0936a-131">Without support for time zone serialization and deserialization, you have little choice but to handle the resulting <xref:System.TimeZoneNotFoundException> by ending the application.</span></span> <span data-ttu-id="0936a-132">不過，藉由使用時區序列化和還原序列化，您可以處理未預期<xref:System.TimeZoneNotFoundException>藉由還原序列化的字串，與應用程式所需的時區將會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0936a-132">However, by using time zone serialization and deserialization, you can handle an unexpected <xref:System.TimeZoneNotFoundException> by restoring the required time zone from a serialized string, and the application will continue to run.</span></span>

<span data-ttu-id="0936a-133">下列範例會建立，並序列化自訂中部標準時間區域。</span><span class="sxs-lookup"><span data-stu-id="0936a-133">The following example creates and serializes a custom Central Standard Time zone.</span></span> <span data-ttu-id="0936a-134">它接著會嘗試從登錄擷取時區中部標準時間。</span><span class="sxs-lookup"><span data-stu-id="0936a-134">It then tries to retrieve the Central Standard Time zone from the registry.</span></span> <span data-ttu-id="0936a-135">如果擷取作業會擲回其中<xref:System.TimeZoneNotFoundException>或<xref:System.InvalidTimeZoneException>，例外狀況處理常式會還原序列化的時區。</span><span class="sxs-lookup"><span data-stu-id="0936a-135">If the retrieval operation throws either a <xref:System.TimeZoneNotFoundException> or an <xref:System.InvalidTimeZoneException>, the exception handler deserializes the time zone.</span></span>

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a><span data-ttu-id="0936a-136">儲存為序列化的字串，並將它在需要時還原</span><span class="sxs-lookup"><span data-stu-id="0936a-136">Storing a serialized string and restoring it when needed</span></span>

<span data-ttu-id="0936a-137">先前的範例有儲存為字串變數的時區資訊，而且需要時還原。</span><span class="sxs-lookup"><span data-stu-id="0936a-137">The previous examples have stored time zone information to a string variable and restored it when needed.</span></span> <span data-ttu-id="0936a-138">不過，包含序列化的時間區域資訊可以儲存在儲存媒體中，例如外部檔案，將資源檔中的字串會內嵌在應用程式或登錄。</span><span class="sxs-lookup"><span data-stu-id="0936a-138">However, the string that contains serialized time zone information can itself be stored in some storage medium, such as an external file, a resource file embedded in the application, or the registry.</span></span> <span data-ttu-id="0936a-139">（請注意自訂時區的相關資訊，應該儲存系統的時區為準的登錄機碼以外）。</span><span class="sxs-lookup"><span data-stu-id="0936a-139">(Note that information about custom time zones should be stored apart from the system's time zone keys in the registry.)</span></span>

<span data-ttu-id="0936a-140">將序列化的時區字串儲存在這種方式也會分隔時區建立常式與應用程式本身。</span><span class="sxs-lookup"><span data-stu-id="0936a-140">Storing a serialized time zone string in this manner also separates the time zone creation routine from the application itself.</span></span> <span data-ttu-id="0936a-141">例如，時區建立常式可以執行，並建立資料檔案，其中包含應用程式可以使用的歷程時區資訊。</span><span class="sxs-lookup"><span data-stu-id="0936a-141">For example, a time zone creation routine can execute and create a data file that contains historical time zone information that an application can use.</span></span> <span data-ttu-id="0936a-142">可以是資料檔，則安裝應用程式時，您可以開啟和一或多個時區可以還原序列化時應用程式需要它們。</span><span class="sxs-lookup"><span data-stu-id="0936a-142">The data file can be then be installed with the application, and it can be opened and one or more of its time zones can be deserialized when the application requires them.</span></span>

<span data-ttu-id="0936a-143">如需用來儲存已序列化的時區資料的內嵌的資源的範例，請參閱[How to： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="0936a-143">For an example that uses an embedded resource to store serialized time zone data, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0936a-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0936a-144">See also</span></span>

[<span data-ttu-id="0936a-145">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="0936a-145">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)

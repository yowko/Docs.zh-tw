---
title: 如何：將時區儲存到內嵌資源
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
ms.openlocfilehash: c8084cb8edff64b9d598f4fd0a62a362491c7aa7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281241"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="13ff5-102">如何：將時區儲存到內嵌資源</span><span class="sxs-lookup"><span data-stu-id="13ff5-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="13ff5-103">時區感知應用程式通常需要有特定的時區。</span><span class="sxs-lookup"><span data-stu-id="13ff5-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="13ff5-104">不過，因為個別物件的可用性 <xref:System.TimeZoneInfo> 取決於儲存在本機系統登錄中的資訊，所以通常可能不會有可用的時區。</span><span class="sxs-lookup"><span data-stu-id="13ff5-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="13ff5-105">此外，使用方法具現化之自訂時區的相關資訊 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 不會與登錄中的其他時區資訊一起儲存。</span><span class="sxs-lookup"><span data-stu-id="13ff5-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="13ff5-106">若要確保這些時區在需要時可供使用，您可以藉由將它們序列化來加以儲存，並在稍後將它們還原序列化來加以還原。</span><span class="sxs-lookup"><span data-stu-id="13ff5-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="13ff5-107">一般來說，將 <xref:System.TimeZoneInfo> 物件序列化會與時區感知應用程式分開。</span><span class="sxs-lookup"><span data-stu-id="13ff5-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="13ff5-108">視用來保存序列化物件的資料存放區 <xref:System.TimeZoneInfo> 而定，時區資料可能會序列化為安裝或安裝常式的一部分（例如，當資料儲存在登錄的應用程式索引鍵中），或做為在編譯最終應用程式之前執行之公用程式常式的一部分（例如，當序列化的資料儲存在 .NET XML 資源（.resx）檔案中時）。</span><span class="sxs-lookup"><span data-stu-id="13ff5-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="13ff5-109">除了以應用程式編譯的資源檔以外，還有其他幾個資料存放區可以用於時區資訊。</span><span class="sxs-lookup"><span data-stu-id="13ff5-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="13ff5-110">這些選項包括：</span><span class="sxs-lookup"><span data-stu-id="13ff5-110">These include the following:</span></span>

- <span data-ttu-id="13ff5-111">登錄。</span><span class="sxs-lookup"><span data-stu-id="13ff5-111">The registry.</span></span> <span data-ttu-id="13ff5-112">請注意，應用程式應該使用自己的應用程式金鑰的子機碼來儲存自訂時區資料，而不是使用 HKEY_LOCAL_MACHINE \Software\microsoft\windows server\ Nt\currentversion\time zones 區域的子機碼。</span><span class="sxs-lookup"><span data-stu-id="13ff5-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

- <span data-ttu-id="13ff5-113">設定檔。</span><span class="sxs-lookup"><span data-stu-id="13ff5-113">Configuration files.</span></span>

- <span data-ttu-id="13ff5-114">其他系統檔案。</span><span class="sxs-lookup"><span data-stu-id="13ff5-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="13ff5-115">若要將時區序列化為 .resx 檔案來儲存該時區</span><span class="sxs-lookup"><span data-stu-id="13ff5-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="13ff5-116">取出現有的時區或建立新的時區。</span><span class="sxs-lookup"><span data-stu-id="13ff5-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="13ff5-117">若要取出現有的時區，請參閱[如何：存取預先定義的 UTC 和當地時區物件](access-utc-and-local.md)和[如何：具現化 TimeZoneInfo 物件](instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="13ff5-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="13ff5-118">若要建立新的時區，請呼叫方法的其中一個多載 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 。</span><span class="sxs-lookup"><span data-stu-id="13ff5-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="13ff5-119">如需詳細資訊，請參閱[如何：建立沒有調整規則的時區](create-time-zones-without-adjustment-rules.md)和[如何：建立具有調整規則的時區](create-time-zones-with-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="13ff5-119">For more information, see [How to: Create time zones without adjustment rules](create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="13ff5-120">呼叫 <xref:System.TimeZoneInfo.ToSerializedString%2A> 方法，以建立包含時區資料的字串。</span><span class="sxs-lookup"><span data-stu-id="13ff5-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="13ff5-121">藉由將 .resx 檔的 <xref:System.IO.StreamWriter> 名稱和選擇性路徑提供給類別的函式，以具現化物件 <xref:System.IO.StreamWriter> 。</span><span class="sxs-lookup"><span data-stu-id="13ff5-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="13ff5-122">藉 <xref:System.Resources.ResXResourceWriter> 由將 <xref:System.IO.StreamWriter> 物件傳遞至類別的函式，來具現化物件 <xref:System.Resources.ResXResourceWriter> 。</span><span class="sxs-lookup"><span data-stu-id="13ff5-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="13ff5-123">將時區的序列化字串傳遞給 <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="13ff5-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="13ff5-124">呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="13ff5-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="13ff5-125">呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="13ff5-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="13ff5-126">藉 <xref:System.IO.StreamWriter> 由呼叫其方法來關閉物件 <xref:System.IO.StreamWriter.Close%2A> 。</span><span class="sxs-lookup"><span data-stu-id="13ff5-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="13ff5-127">將產生的 .resx 檔案加入至應用程式的 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="13ff5-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="13ff5-128">使用 Visual Studio 中的 [**屬性**] 視窗，確保 .resx 檔案的 [**組建動作**] 屬性設定為 [**內嵌資源**]。</span><span class="sxs-lookup"><span data-stu-id="13ff5-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="13ff5-129">範例</span><span class="sxs-lookup"><span data-stu-id="13ff5-129">Example</span></span>

<span data-ttu-id="13ff5-130">下列範例 <xref:System.TimeZoneInfo> 會將代表中部標準時間的物件，以及 <xref:System.TimeZoneInfo> 代表 Palmer 站的物件（南極洲 Time）序列化為名為 SerializedTimeZones 的 .net XML 資源檔。</span><span class="sxs-lookup"><span data-stu-id="13ff5-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="13ff5-131">中央標準時間通常會在登錄中定義;Palmer 站，南極洲是自訂的時區。</span><span class="sxs-lookup"><span data-stu-id="13ff5-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="13ff5-132">這個範例 <xref:System.TimeZoneInfo> 會序列化物件，使其在編譯時期於資源檔中提供。</span><span class="sxs-lookup"><span data-stu-id="13ff5-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="13ff5-133">因為 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法會將完整的標頭資訊新增至 .NET XML 資源檔，所以不能用來將資源新增至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="13ff5-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="13ff5-134">這個範例會藉由檢查 SerializedTimeZones .resx 檔案來處理這項工作，如果存在，則會將這兩個序列化時區以外的所有資源儲存至泛型 <xref:System.Collections.Generic.Dictionary%602> 物件。</span><span class="sxs-lookup"><span data-stu-id="13ff5-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="13ff5-135">然後會刪除現有的檔案，並將現有的資源新增至新的 SerializedTimeZones .resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="13ff5-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="13ff5-136">序列化的時區資料也會新增至這個檔案。</span><span class="sxs-lookup"><span data-stu-id="13ff5-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="13ff5-137">資源的索引鍵（或**名稱**）欄位不應包含內嵌空格。</span><span class="sxs-lookup"><span data-stu-id="13ff5-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="13ff5-138">在 <xref:System.String.Replace%28System.String%2CSystem.String%29> 指派給資源檔之前，會呼叫方法來移除時區識別碼中的所有內嵌空格。</span><span class="sxs-lookup"><span data-stu-id="13ff5-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="13ff5-139">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="13ff5-139">Compiling the code</span></span>

<span data-ttu-id="13ff5-140">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="13ff5-140">This example requires:</span></span>

- <span data-ttu-id="13ff5-141">系統會將對 System.web 和 system.string 的參考加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="13ff5-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="13ff5-142">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="13ff5-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="13ff5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13ff5-143">See also</span></span>

- [<span data-ttu-id="13ff5-144">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="13ff5-144">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="13ff5-145">時區總覽</span><span class="sxs-lookup"><span data-stu-id="13ff5-145">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="13ff5-146">如何：從內嵌資源還原時區</span><span class="sxs-lookup"><span data-stu-id="13ff5-146">How to: Restore time zones from an embedded resource</span></span>](restore-time-zones-from-an-embedded-resource.md)

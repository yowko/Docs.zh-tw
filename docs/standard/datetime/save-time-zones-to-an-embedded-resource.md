---
title: HOW TO：將時區儲存到內嵌資源
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67a97193d186275e6a788f6b18bbc17c535f367
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912700"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="3a4a2-102">HOW TO：將時區儲存到內嵌資源</span><span class="sxs-lookup"><span data-stu-id="3a4a2-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="3a4a2-103">時區感知的應用程式通常需要為特定時區的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="3a4a2-104">不過，因為個別的可用性<xref:System.TimeZoneInfo>物件取決於儲存在本機系統登錄中的資訊，甚至是通常可用的時區可能不存在。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="3a4a2-105">此外，自訂時區的相關資訊，將使用具現化<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會儲存在登錄中的其他時區資訊。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="3a4a2-106">若要確保的這些時間的時區都可在必要時，序列化，就可以將它儲存它們即可稍後再還原序列化其還原。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="3a4a2-107">一般而言，序列化<xref:System.TimeZoneInfo>物件除了時區感知的應用程式，就會發生。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="3a4a2-108">根據資料存放區用來保存序列化<xref:System.TimeZoneInfo>物件時，可能會序列化時區的資料，設定或安裝的常式 （例如，當資料儲存在登錄的應用程式金鑰），或執行公用程式常式之前 （例如，當序列化的資料儲存在.NET XML 資源 (.resx) 檔），最終的應用程式會編譯。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="3a4a2-109">除了編譯與應用程式的資源檔，數個其他資料存放區可用的時區資訊。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="3a4a2-110">這些需求包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="3a4a2-110">These include the following:</span></span>

* <span data-ttu-id="3a4a2-111">登錄中。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-111">The registry.</span></span> <span data-ttu-id="3a4a2-112">請注意，應用程式應該使用它自己的應用程式金鑰的子機碼來儲存自訂的時區資料，而不是使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones 的子機碼。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="3a4a2-113">組態檔。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-113">Configuration files.</span></span>

* <span data-ttu-id="3a4a2-114">其他系統檔案。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="3a4a2-115">序列化至.resx 檔案所儲存的時區</span><span class="sxs-lookup"><span data-stu-id="3a4a2-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="3a4a2-116">擷取現有的時區，或建立新的時區。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="3a4a2-117">若要擷取現有的時區，請參閱[How to:存取預先定義的 UTC 和當地時區物件](../../../docs/standard/datetime/access-utc-and-local.md)和[How to:將 TimeZoneInfo 物件具現化](../../../docs/standard/datetime/instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="3a4a2-118">若要建立新的時區，請呼叫其中一個多載<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="3a4a2-119">如需詳細資訊，請參閱[如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[How to:建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="3a4a2-120">呼叫<xref:System.TimeZoneInfo.ToSerializedString%2A>方法用來建立字串，包含時區的資料。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="3a4a2-121">具現化<xref:System.IO.StreamWriter>藉由提供名稱和選擇性的.resx 檔案的路徑物件<xref:System.IO.StreamWriter>類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="3a4a2-122">具現化<xref:System.Resources.ResXResourceWriter>物件，並傳遞<xref:System.IO.StreamWriter>物件到<xref:System.Resources.ResXResourceWriter>類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="3a4a2-123">傳遞時區的序列化字串<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="3a4a2-124">呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="3a4a2-125">呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="3a4a2-126">關閉<xref:System.IO.StreamWriter>物件，藉由呼叫其<xref:System.IO.StreamWriter.Close%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="3a4a2-127">將產生的.resx 檔案新增至應用程式的 Visual Studio 專案。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="3a4a2-128">使用**屬性**視窗，在 Visual Studio 中，請確定.resx 檔**建置動作**屬性設定為**內嵌資源**。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="3a4a2-129">範例</span><span class="sxs-lookup"><span data-stu-id="3a4a2-129">Example</span></span>

<span data-ttu-id="3a4a2-130">下列範例會序列化<xref:System.TimeZoneInfo>物件，表示中部標準時間和<xref:System.TimeZoneInfo>物件，表示.NET XML 資源檔名為 SerializedTimeZones.resx 帕麥站，南極大陸的時間。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="3a4a2-131">中部標準時間通常被定義在登錄中;帕麥站，南極大陸是自訂的時區。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="3a4a2-132">此範例會序列化<xref:System.TimeZoneInfo>物件，讓它們可在資源檔編譯時期。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="3a4a2-133">因為<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>方法將完整的標頭資訊新增至.NET XML 資源檔，它不能將資源新增至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="3a4a2-134">範例會處理這藉由檢查 SerializedTimeZones.resx 檔案，且若有的話，儲存其所有資源以外的其他兩個都序列化成泛型的時區<xref:System.Collections.Generic.Dictionary%602>物件。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="3a4a2-135">現有的檔案會被刪除，現有的資源會新增至新的 SerializedTimeZones.resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="3a4a2-136">序列化的時區資料也會加入至這個檔案。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="3a4a2-137">索引鍵 (或**名稱**) 資源的欄位不應包含內嵌的空格。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="3a4a2-138"><xref:System.String.Replace%28System.String%2CSystem.String%29>呼叫方法先指派給資源檔，時區識別項中移除所有內嵌的空格。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="3a4a2-139">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3a4a2-139">Compiling the code</span></span>

<span data-ttu-id="3a4a2-140">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="3a4a2-140">This example requires:</span></span>

* <span data-ttu-id="3a4a2-141">System.Windows.Forms.dll 和 System.Core.dll 的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="3a4a2-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="3a4a2-142">下列命名空間會匯入：</span><span class="sxs-lookup"><span data-stu-id="3a4a2-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="3a4a2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a4a2-143">See also</span></span>

- [<span data-ttu-id="3a4a2-144">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="3a4a2-144">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="3a4a2-145">時區概觀</span><span class="sxs-lookup"><span data-stu-id="3a4a2-145">Time zone overview</span></span>](../../../docs/standard/datetime/time-zone-overview.md)
- [<span data-ttu-id="3a4a2-146">如何：從內嵌資源還原時區</span><span class="sxs-lookup"><span data-stu-id="3a4a2-146">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)

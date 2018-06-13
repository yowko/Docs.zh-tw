---
title: 如何： 將時區儲存到內嵌資源
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
ms.openlocfilehash: 4dd7e6db78b76d737cb4646c2fad79d96fb60aee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576265"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a><span data-ttu-id="5d8cc-102">如何： 將時區儲存到內嵌資源</span><span class="sxs-lookup"><span data-stu-id="5d8cc-102">How to: Save time zones to an embedded resource</span></span>

<span data-ttu-id="5d8cc-103">時區感知應用程式通常需要有特定的時區。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-103">A time zone-aware application often requires the presence of a particular time zone.</span></span> <span data-ttu-id="5d8cc-104">不過，因為個別的可用性<xref:System.TimeZoneInfo>物件相依於儲存在本機系統登錄中的資訊，甚至是通常可用的時區可能不存在。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-104">However, because the availability of individual <xref:System.TimeZoneInfo> objects depends on information stored in the local system's registry, even customarily available time zones may be absent.</span></span> <span data-ttu-id="5d8cc-105">此外，自訂時區的相關資訊，將使用具現化<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會儲存在登錄中的其他時區資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-105">In addition, information about custom time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method is not stored with other time zone information in the registry.</span></span> <span data-ttu-id="5d8cc-106">若要確保這些時間區域，可在必要時，您可以序列化，將它們儲存，並稍後再還原其還原序列化。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-106">To ensure that these time zones are available when they are needed, you can save them by serializing them, and later restore them by deserializing them.</span></span>

<span data-ttu-id="5d8cc-107">一般來說，序列化<xref:System.TimeZoneInfo>物件除了時區感知的應用程式，就會發生。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-107">Typically, serializing a <xref:System.TimeZoneInfo> object occurs apart from the time zone-aware application.</span></span> <span data-ttu-id="5d8cc-108">根據用來保存已序列化的資料存放區<xref:System.TimeZoneInfo>物件，可能會序列化時區的資料，設定或安裝常式 （例如，當資料儲存在登錄的應用程式金鑰），或執行公用程式常式之前完成的應用程式會編譯 （例如，當序列化的資料儲存在.NET XML 資源 (.resx) 檔）。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-108">Depending on the data store used to hold serialized <xref:System.TimeZoneInfo> objects, time zone data may be serialized as part of a setup or installation routine (for example, when the data is stored in an application key of the registry), or as part of a utility routine that runs before the final application is compiled (for example, when the serialized data is stored in a .NET XML resource (.resx) file).</span></span>

<span data-ttu-id="5d8cc-109">除了與應用程式會編譯資源檔，數個其他資料存放區可以用於時區資訊。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-109">In addition to a resource file that is compiled with the application, several other data stores can be used for time zone information.</span></span> <span data-ttu-id="5d8cc-110">這些需求包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="5d8cc-110">These include the following:</span></span>

* <span data-ttu-id="5d8cc-111">登錄中。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-111">The registry.</span></span> <span data-ttu-id="5d8cc-112">請注意，應用程式應該使用它自己的應用程式金鑰的子機碼來儲存自訂的時區資料，而不是使用 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time 區域的子機碼。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-112">Note that an application should use the subkeys of its own application key to store custom time zone data rather than using the subkeys of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones.</span></span>

* <span data-ttu-id="5d8cc-113">組態檔。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-113">Configuration files.</span></span>

* <span data-ttu-id="5d8cc-114">其他系統檔案。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-114">Other system files.</span></span>

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a><span data-ttu-id="5d8cc-115">要儲存時區序列化至.resx 檔案</span><span class="sxs-lookup"><span data-stu-id="5d8cc-115">To save a time zone by serializing it to a .resx file</span></span>

1. <span data-ttu-id="5d8cc-116">擷取現有的時區，或建立新的時區。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-116">Retrieve an existing time zone or create a new time zone.</span></span>

   <span data-ttu-id="5d8cc-117">若要擷取現有的時區，請參閱[如何： 存取預先定義的 UTC 與本地時間區域物件](../../../docs/standard/datetime/access-utc-and-local.md)和[如何： 具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-117">To retrieve an existing time zone, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) and [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

   <span data-ttu-id="5d8cc-118">若要建立新的時區，請呼叫其中一個多載的<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-118">To create a new time zone, call one of the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="5d8cc-119">如需詳細資訊，請參閱[How to： 建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)和[How to： 建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-119">For more information, see [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

2. <span data-ttu-id="5d8cc-120">呼叫<xref:System.TimeZoneInfo.ToSerializedString%2A>方法來建立字串，包含時區的資料。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-120">Call the <xref:System.TimeZoneInfo.ToSerializedString%2A> method to create a string that contains the time zone's data.</span></span>

3. <span data-ttu-id="5d8cc-121">具現化<xref:System.IO.StreamWriter>藉由提供名稱和選擇性的.resx 檔案的路徑物件<xref:System.IO.StreamWriter>類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-121">Instantiate a <xref:System.IO.StreamWriter> object by providing the name and optionally the path of the .resx file to the <xref:System.IO.StreamWriter> class constructor.</span></span>

4. <span data-ttu-id="5d8cc-122">具現化<xref:System.Resources.ResXResourceWriter>物件，並傳遞<xref:System.IO.StreamWriter>物件<xref:System.Resources.ResXResourceWriter>類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-122">Instantiate a <xref:System.Resources.ResXResourceWriter> object by passing the <xref:System.IO.StreamWriter> object to the <xref:System.Resources.ResXResourceWriter> class constructor.</span></span>

5. <span data-ttu-id="5d8cc-123">傳遞時區的序列化字串<xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-123">Pass the time zone's serialized string to the <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> method.</span></span>

6. <span data-ttu-id="5d8cc-124">呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-124">Call the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method.</span></span>

7. <span data-ttu-id="5d8cc-125">呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-125">Call the <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> method.</span></span>

8. <span data-ttu-id="5d8cc-126">關閉<xref:System.IO.StreamWriter>物件藉由呼叫其<xref:System.IO.StreamWriter.Close%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-126">Close the <xref:System.IO.StreamWriter> object by calling its <xref:System.IO.StreamWriter.Close%2A> method.</span></span>

9. <span data-ttu-id="5d8cc-127">加入應用程式的 Visual Studio 專案中產生的.resx 檔。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-127">Add the generated .resx file to the application's Visual Studio project.</span></span>

10. <span data-ttu-id="5d8cc-128">使用**屬性**視窗在 Visual Studio 中，請確定.resx 檔**建置動作**屬性設定為**內嵌資源**。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-128">Using the **Properties** window in Visual Studio, make sure that the .resx file's **Build Action** property is set to **Embedded Resource**.</span></span>

## <a name="example"></a><span data-ttu-id="5d8cc-129">範例</span><span class="sxs-lookup"><span data-stu-id="5d8cc-129">Example</span></span>

<span data-ttu-id="5d8cc-130">下列範例會序列化<xref:System.TimeZoneInfo>中部標準時間表示的物件和<xref:System.TimeZoneInfo>物件，代表名為 SerializedTimeZones.resx.NET XML 資源檔 Palmer 站台、 目前時間。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-130">The following example serializes a <xref:System.TimeZoneInfo> object that represents Central Standard Time and a <xref:System.TimeZoneInfo> object that represents the Palmer Station, Antarctica time to a .NET XML resource file that is named SerializedTimeZones.resx.</span></span> <span data-ttu-id="5d8cc-131">中部標準時間通常被定義在登錄中。Palmer 站台目前是自訂的時區。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-131">Central Standard Time is typically defined in the registry; Palmer Station, Antarctica is a custom time zone.</span></span>

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

<span data-ttu-id="5d8cc-132">這個範例會序列化<xref:System.TimeZoneInfo>物件，以便他們可以使用資源檔中在編譯時間。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-132">This example serializes <xref:System.TimeZoneInfo> objects so that they are available in a resource file at compile time.</span></span>

<span data-ttu-id="5d8cc-133">因為<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>方法將完整的標頭資訊.NET XML 資源檔，但它不能將資源加入至現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-133">Because the <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> method adds complete header information to a .NET XML resource file, it cannot be used to add resources to an existing file.</span></span> <span data-ttu-id="5d8cc-134">此範例會藉由檢查 SerializedTimeZones.resx 檔案處理這，如果存在的話，其所有資源以外的儲存兩個都序列化泛型時區<xref:System.Collections.Generic.Dictionary%602>物件。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-134">The example handles this by checking for the SerializedTimeZones.resx file and, if it exists, storing all of its resources other than the two serialized time zones to a generic <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="5d8cc-135">現有的檔案會被刪除，現有的資源新增至新的 SerializedTimeZones.resx 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-135">The existing file is then deleted and the existing resources are added to a new SerializedTimeZones.resx file.</span></span> <span data-ttu-id="5d8cc-136">已序列化的時區資料也會加入至這個檔案。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-136">The serialized time zone data is also added to this file.</span></span>

<span data-ttu-id="5d8cc-137">索引鍵 (或**名稱**) 的資源欄位不能包含內嵌的空格。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-137">The key (or **Name**) fields of resources should not contain embedded spaces.</span></span> <span data-ttu-id="5d8cc-138"><xref:System.String.Replace%28System.String%2CSystem.String%29>方法呼叫之前就會指派給資源檔，時區識別項中移除所有內嵌的空格。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-138">The <xref:System.String.Replace%28System.String%2CSystem.String%29> method is called to remove all embedded spaces in the time zone identifiers before they are assigned to the resource file.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="5d8cc-139">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5d8cc-139">Compiling the code</span></span>

<span data-ttu-id="5d8cc-140">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="5d8cc-140">This example requires:</span></span>

* <span data-ttu-id="5d8cc-141">System.Windows.Forms.dll 和 System.Core.dll 的參考加入專案。</span><span class="sxs-lookup"><span data-stu-id="5d8cc-141">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="5d8cc-142">應該是匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="5d8cc-142">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="5d8cc-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d8cc-143">See also</span></span>

<span data-ttu-id="5d8cc-144">[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="5d8cc-144">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)</span></span>

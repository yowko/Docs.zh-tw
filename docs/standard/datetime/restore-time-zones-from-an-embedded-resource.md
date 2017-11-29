---
title: "如何： 從內嵌資源還原時區"
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
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db4f2ae40d25795b0e5f75ac3612f45834043dfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="38508-102">如何： 從內嵌資源還原時區</span><span class="sxs-lookup"><span data-stu-id="38508-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="38508-103">本主題說明如何還原已儲存在資源檔中的時區。</span><span class="sxs-lookup"><span data-stu-id="38508-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="38508-104">資訊和儲存時區的相關指示，請參閱[How to： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="38508-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="38508-105">從內嵌資源 TimeZoneInfo 物件還原序列化</span><span class="sxs-lookup"><span data-stu-id="38508-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="38508-106">如果要擷取時區不是自訂的時區，請嘗試使用具現化<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="38508-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="38508-107">具現化<xref:System.Resources.ResourceManager>完整限定的名稱的內嵌的資源檔和包含的資源檔的組件的參考傳遞的物件。</span><span class="sxs-lookup"><span data-stu-id="38508-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="38508-108">如果您無法判斷內嵌的資源檔的完整限定的名稱，請使用[Ildasm.exe （IL 解譯器）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)來檢查組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="38508-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="38508-109">`.mresource`項目識別的資源。</span><span class="sxs-lookup"><span data-stu-id="38508-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="38508-110">在範例中，資源的完整格式的名稱是`SerializeTimeZoneData.SerializedTimeZones`。</span><span class="sxs-lookup"><span data-stu-id="38508-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="38508-111">如果相同的組件包含時區具現化程式碼內嵌資源檔，您可以藉由呼叫來擷取它的參考`static`(`Shared`在 Visual Basic 中)<xref:System.Reflection.Assembly.GetExecutingAssembly%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="38508-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="38508-112">如果呼叫<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>方法失敗，或如果自訂的時區來具現化時，擷取字串，包含已序列化的時區，藉由呼叫<xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="38508-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="38508-113">將時區資料還原序列化呼叫<xref:System.TimeZoneInfo.FromSerializedString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="38508-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="38508-114">範例</span><span class="sxs-lookup"><span data-stu-id="38508-114">Example</span></span>

<span data-ttu-id="38508-115">下列範例會還原序列化<xref:System.TimeZoneInfo>儲存內嵌的.NET XML 資源檔中的物件。</span><span class="sxs-lookup"><span data-stu-id="38508-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="38508-116">此程式碼說明例外狀況處理，以確保<xref:System.TimeZoneInfo>應用程式所需的物件已存在。</span><span class="sxs-lookup"><span data-stu-id="38508-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="38508-117">它會先嘗試具現化<xref:System.TimeZoneInfo>物件擷取登錄使用<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="38508-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="38508-118">如果無法具現化時區，程式碼會擷取它從內嵌的資源檔。</span><span class="sxs-lookup"><span data-stu-id="38508-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="38508-119">因為自訂時區的資料 (使用具現化時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法) 不會儲存在登錄中，程式碼不會呼叫<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>至 Palmer，南極洲，具現化時區。</span><span class="sxs-lookup"><span data-stu-id="38508-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="38508-120">相反地，它立即會內嵌的資源檔擷取字串，包含時區的資料，然後呼叫<xref:System.TimeZoneInfo.FromSerializedString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="38508-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="38508-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="38508-121">Compiling the code</span></span>

<span data-ttu-id="38508-122">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="38508-122">This example requires:</span></span>

* <span data-ttu-id="38508-123">System.Windows.Forms.dll 和 System.Core.dll 的參考加入專案。</span><span class="sxs-lookup"><span data-stu-id="38508-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="38508-124">應該是匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="38508-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="38508-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="38508-125">See also</span></span>

<span data-ttu-id="38508-126">[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
[How to： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span><span class="sxs-lookup"><span data-stu-id="38508-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)</span></span>

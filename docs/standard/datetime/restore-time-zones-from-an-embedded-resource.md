---
title: 作法：從內嵌資源還原時區
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: a1302f595a0907103bae2695e703e5af6da660a7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817662"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a><span data-ttu-id="ca722-102">作法：從內嵌資源還原時區</span><span class="sxs-lookup"><span data-stu-id="ca722-102">How to: Restore time zones from an embedded resource</span></span>

<span data-ttu-id="ca722-103">本主題說明如何還原已儲存在資源檔中的時區。</span><span class="sxs-lookup"><span data-stu-id="ca722-103">This topic describes how to restore time zones that have been saved in a resource file.</span></span> <span data-ttu-id="ca722-104">如需儲存時區的詳細資訊和指示，請參閱 [如何：將時區儲存到內嵌資源](save-time-zones-to-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="ca722-104">For information and instructions about saving time zones, see [How to: Save time zones to an embedded resource](save-time-zones-to-an-embedded-resource.md).</span></span>

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a><span data-ttu-id="ca722-105">從內嵌資源還原序列化 TimeZoneInfo 物件</span><span class="sxs-lookup"><span data-stu-id="ca722-105">To deserialize a TimeZoneInfo object from an embedded resource</span></span>

1. <span data-ttu-id="ca722-106">如果要取出的時區不是自訂時區，請嘗試使用方法將它具現化 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ca722-106">If the time zone to be retrieved is not a custom time zone, try to instantiate it by using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span>

2. <span data-ttu-id="ca722-107">藉 <xref:System.Resources.ResourceManager> 由傳遞內嵌資源檔的完整名稱，以及包含資源檔之元件的參考，來具現化物件。</span><span class="sxs-lookup"><span data-stu-id="ca722-107">Instantiate a <xref:System.Resources.ResourceManager> object by passing the fully qualified name of the embedded resource file and a reference to the assembly that contains the resource file.</span></span>

   <span data-ttu-id="ca722-108">如果您無法判斷內嵌資源檔的完整名稱，請使用 [Ildasm.exe (IL ](../../framework/tools/ildasm-exe-il-disassembler.md) 解譯器) 檢查元件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="ca722-108">If you cannot determine the fully qualified name of the embedded resource file, use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's manifest.</span></span> <span data-ttu-id="ca722-109">`.mresource`專案會識別資源。</span><span class="sxs-lookup"><span data-stu-id="ca722-109">An `.mresource` entry identifies the resource.</span></span> <span data-ttu-id="ca722-110">在此範例中，資源的完整名稱為 `SerializeTimeZoneData.SerializedTimeZones` 。</span><span class="sxs-lookup"><span data-stu-id="ca722-110">In the example, the resource's fully qualified name is `SerializeTimeZoneData.SerializedTimeZones`.</span></span>

   <span data-ttu-id="ca722-111">如果資源檔內嵌在包含時區具現化程式碼的相同元件中，您可以 `static` `Shared` 在 Visual Basic) 方法中呼叫 (，以抓取它的參考 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ca722-111">If the resource file is embedded in the same assembly that contains the time zone instantiation code, you can retrieve a reference to it by calling the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method.</span></span>

3. <span data-ttu-id="ca722-112">如果方法的呼叫 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 失敗，或是要具現化自訂時區，請呼叫方法來取出包含序列化時區的字串 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ca722-112">If the call to the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method fails, or if a custom time zone is to be instantiated, retrieve a string that contains the serialized time zone by calling the <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="ca722-113">藉由呼叫方法將時區資料還原序列化 <xref:System.TimeZoneInfo.FromSerializedString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ca722-113">Deserialize the time zone data by calling the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="example"></a><span data-ttu-id="ca722-114">範例</span><span class="sxs-lookup"><span data-stu-id="ca722-114">Example</span></span>

<span data-ttu-id="ca722-115">下列範例會將 <xref:System.TimeZoneInfo> 儲存在內嵌 .NET XML 資源檔中的物件還原序列化。</span><span class="sxs-lookup"><span data-stu-id="ca722-115">The following example deserializes a <xref:System.TimeZoneInfo> object stored in an embedded .NET XML resource file.</span></span>

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

<span data-ttu-id="ca722-116">這段程式碼示範例外狀況處理，以確保 <xref:System.TimeZoneInfo> 應用程式所需的物件存在。</span><span class="sxs-lookup"><span data-stu-id="ca722-116">This code illustrates exception handling to ensure that a <xref:System.TimeZoneInfo> object required by the application is present.</span></span> <span data-ttu-id="ca722-117">它會先嘗試 <xref:System.TimeZoneInfo> 使用方法從登錄中取出物件來將它具現化 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ca722-117">It first tries to instantiate a <xref:System.TimeZoneInfo> object by retrieving it from the registry using the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method.</span></span> <span data-ttu-id="ca722-118">如果無法將時區具現化，則程式碼會從內嵌的資源檔中取出。</span><span class="sxs-lookup"><span data-stu-id="ca722-118">If the time zone cannot be instantiated, the code retrieves it from the embedded resource file.</span></span>

<span data-ttu-id="ca722-119">由於自訂時區的資料 (使用方法所具現化的時區 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>) 不會儲存在登錄中，因此程式碼不會呼叫來具現 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 化 Palmer、南極洲的時區。</span><span class="sxs-lookup"><span data-stu-id="ca722-119">Because data for custom time zones (time zones instantiated by using the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method) are not stored in the registry, the code does not call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> to instantiate the time zone for Palmer, Antarctica.</span></span> <span data-ttu-id="ca722-120">相反地，它會立即查看內嵌資源檔，以在呼叫方法之前，先取出包含時區資料的字串 <xref:System.TimeZoneInfo.FromSerializedString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ca722-120">Instead, it immediately looks to the embedded resource file to retrieve a string that contains the time zone's data before it calls the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="ca722-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ca722-121">Compiling the code</span></span>

<span data-ttu-id="ca722-122">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ca722-122">This example requires:</span></span>

- <span data-ttu-id="ca722-123">將 System.Windows.Forms.dll 和 System.Core.dll 的參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="ca722-123">That a reference to System.Windows.Forms.dll and System.Core.dll be added to the project.</span></span>

- <span data-ttu-id="ca722-124">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="ca722-124">That the following namespaces be imported:</span></span>

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a><span data-ttu-id="ca722-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca722-125">See also</span></span>

- [<span data-ttu-id="ca722-126">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="ca722-126">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="ca722-127">時區概觀</span><span class="sxs-lookup"><span data-stu-id="ca722-127">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="ca722-128">如何：將時區儲存到內嵌資源</span><span class="sxs-lookup"><span data-stu-id="ca722-128">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)

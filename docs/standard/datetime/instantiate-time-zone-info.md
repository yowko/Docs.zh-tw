---
title: HOW TO：將 TimeZoneInfo 物件具現化
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c8ff38325e26dd1bc946f6f12c365b6dea3e228
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669169"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="695ea-102">HOW TO：將 TimeZoneInfo 物件具現化</span><span class="sxs-lookup"><span data-stu-id="695ea-102">How to: Instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="695ea-103">若要將 <xref:System.TimeZoneInfo> 物件具現化，最常見的方式是從登錄擷取其相關資訊。</span><span class="sxs-lookup"><span data-stu-id="695ea-103">The most common way to instantiate a <xref:System.TimeZoneInfo> object is to retrieve information about it from the registry.</span></span> <span data-ttu-id="695ea-104">本主題討論如何將 <xref:System.TimeZoneInfo> 物件從本機系統登錄具現化。</span><span class="sxs-lookup"><span data-stu-id="695ea-104">This topic discusses how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

### <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="695ea-105">將 TimeZoneInfo 物件具現化</span><span class="sxs-lookup"><span data-stu-id="695ea-105">To instantiate a TimeZoneInfo object</span></span>

1. <span data-ttu-id="695ea-106">宣告 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="695ea-106">Declare a <xref:System.TimeZoneInfo> object.</span></span>

2. <span data-ttu-id="695ea-107">呼叫 `static` (Visual Basic 中的`Shared` ) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="695ea-107">Call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method.</span></span>

3. <span data-ttu-id="695ea-108">處理由方法擲回的任何例外狀況，尤其是登錄中未定義時區時所擲回的 <xref:System.TimeZoneNotFoundException> 。</span><span class="sxs-lookup"><span data-stu-id="695ea-108">Handle any exceptions thrown by the method, particularly the <xref:System.TimeZoneNotFoundException> that is thrown if the time zone is not defined in the registry.</span></span>

## <a name="example"></a><span data-ttu-id="695ea-109">範例</span><span class="sxs-lookup"><span data-stu-id="695ea-109">Example</span></span>

<span data-ttu-id="695ea-110">下列程式碼會擷取 <xref:System.TimeZoneInfo> 物件，其代表美加東部標準時間區域，並顯示與本地時間對應的美加東部標準時間。</span><span class="sxs-lookup"><span data-stu-id="695ea-110">The following code retrieves a <xref:System.TimeZoneInfo> object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<span data-ttu-id="695ea-111"><xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> 方法的單一參數是您想要擷取之時區的識別項，其對應至物件的 <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="695ea-111">The <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="695ea-112">時區識別項是唯一識別時區的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="695ea-112">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="695ea-113">雖然大部分的索引鍵相對較短，但時區識別項相較之下就很長。</span><span class="sxs-lookup"><span data-stu-id="695ea-113">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="695ea-114">在大部分情況下，其值會對應到 <xref:System.TimeZoneInfo.StandardName%2A> 物件的 <xref:System.TimeZoneInfo> 屬性，其用來提供時區標準時間的名稱。</span><span class="sxs-lookup"><span data-stu-id="695ea-114">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A> property of a <xref:System.TimeZoneInfo> object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="695ea-115">不過仍有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="695ea-115">However, there are exceptions.</span></span> <span data-ttu-id="695ea-116">若要確定您提供了有效的識別項，最好的方法是列舉系統上可用的時區，並記下存在於其之上的時區識別項。</span><span class="sxs-lookup"><span data-stu-id="695ea-116">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="695ea-117">如需圖例，請參閱[How to:列舉電腦上展示的時區](../../../docs/standard/datetime/enumerate-time-zones.md)。</span><span class="sxs-lookup"><span data-stu-id="695ea-117">For an illustration, see [How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md).</span></span> <span data-ttu-id="695ea-118"> [尋找定義於本機系統的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) 主題同時包含所選取的時區識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="695ea-118">The [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="695ea-119">如果找到時區，此方法會傳回其 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="695ea-119">If the time zone is found, the method returns its <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="695ea-120">如果找不到時區，方法會擲回 <xref:System.TimeZoneNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="695ea-120">If the time zone is not found, the method throws a <xref:System.TimeZoneNotFoundException>.</span></span> <span data-ttu-id="695ea-121">如果找到時區，但其資料已損毀或不完整，則方法會擲回 <xref:System.InvalidTimeZoneException>。</span><span class="sxs-lookup"><span data-stu-id="695ea-121">If the time zone is found but its data is corrupted or incomplete, the method throws an <xref:System.InvalidTimeZoneException>.</span></span>

<span data-ttu-id="695ea-122">如果您的應用程式依賴於必須存在的時區，則您應該先呼叫 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 方法，以便從登錄擷取時區資訊。</span><span class="sxs-lookup"><span data-stu-id="695ea-122">If your application relies on a time zone that must be present, you should first call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method to retrieve the time zone information from the registry.</span></span> <span data-ttu-id="695ea-123">如果方法呼叫失敗，則例外狀況處理常式應建立新的時區執行個體，或透過將序列化 <xref:System.TimeZoneInfo> 物件還原序列化，以重新建立時區執行個體。</span><span class="sxs-lookup"><span data-stu-id="695ea-123">If the method call fails, your exception handler should then either create a new instance of the time zone or re-create it by deserializing a serialized <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="695ea-124">請參閱[如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)的範例。</span><span class="sxs-lookup"><span data-stu-id="695ea-124">See [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) for an example.</span></span>

## <a name="see-also"></a><span data-ttu-id="695ea-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="695ea-125">See also</span></span>

- [<span data-ttu-id="695ea-126">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="695ea-126">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="695ea-127">尋找定義於本機系統的時區</span><span class="sxs-lookup"><span data-stu-id="695ea-127">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="695ea-128">如何：存取預先定義的 UTC 和當地時區物件</span><span class="sxs-lookup"><span data-stu-id="695ea-128">How to: Access the predefined UTC and local time zone objects</span></span>](../../../docs/standard/datetime/access-utc-and-local.md)

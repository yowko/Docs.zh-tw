---
title: HOW TO：存取預先定義的 UTC 和當地時區物件
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa19118ce0837b9ce0eb523f3e086fcbcecb9e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106557"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="c4816-102">作法：存取預先定義的 UTC 和當地時區物件</span><span class="sxs-lookup"><span data-stu-id="c4816-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="c4816-103">類別提供兩個屬性: <xref:System.TimeZoneInfo.Utc%2A>和<xref:System.TimeZoneInfo.Local%2A>, 讓您的程式碼能夠存取預先定義的時區物件。 <xref:System.TimeZoneInfo></span><span class="sxs-lookup"><span data-stu-id="c4816-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="c4816-104">本主題討論如何存取這些屬性所傳回的 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="c4816-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="c4816-105">存取國際標準時間 (UTC) TimeZoneInfo 物件</span><span class="sxs-lookup"><span data-stu-id="c4816-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="c4816-106">`static`使用 (`Shared`在 Visual Basic 中) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性來存取國際標準時間。</span><span class="sxs-lookup"><span data-stu-id="c4816-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="c4816-107">請繼續<xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>透過屬性來存取國際標準時間, 而不是將屬性傳回的物件指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="c4816-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="c4816-108">存取當地時區</span><span class="sxs-lookup"><span data-stu-id="c4816-108">To access the local time zone</span></span>

1. <span data-ttu-id="c4816-109">`static`使用 (`Shared`在 Visual Basic 中) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性來存取本機系統時區。</span><span class="sxs-lookup"><span data-stu-id="c4816-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="c4816-110">請繼續<xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>透過屬性來存取當地時區, 而不是將屬性傳回的物件指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="c4816-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="c4816-111">範例</span><span class="sxs-lookup"><span data-stu-id="c4816-111">Example</span></span>

<span data-ttu-id="c4816-112">下列程式碼會使用 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 和 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。</span><span class="sxs-lookup"><span data-stu-id="c4816-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="c4816-113">您應該一律透過<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性<xref:System.TimeZoneInfo>來存取當地時區, 而不是將當地時區指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="c4816-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="c4816-114">同樣地, 您應該一律透過<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性存取國際標準時間, 而不是將 UTC 區域指派<xref:System.TimeZoneInfo>給物件變數。</span><span class="sxs-lookup"><span data-stu-id="c4816-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="c4816-115">這可避免<xref:System.TimeZoneInfo>物件變數因呼叫<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法而失效。</span><span class="sxs-lookup"><span data-stu-id="c4816-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c4816-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c4816-116">Compiling the code</span></span>

<span data-ttu-id="c4816-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c4816-117">This example requires:</span></span>

- <span data-ttu-id="c4816-118">使用語句匯入的<xref:System>命名空間 (在程式碼C#中為必要項)。 `using`</span><span class="sxs-lookup"><span data-stu-id="c4816-118">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4816-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4816-119">See also</span></span>

- [<span data-ttu-id="c4816-120">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="c4816-120">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="c4816-121">尋找定義於本機系統的時區</span><span class="sxs-lookup"><span data-stu-id="c4816-121">Finding the time zones defined on a local system</span></span>](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="c4816-122">如何：具現化 TimeZoneInfo 物件</span><span class="sxs-lookup"><span data-stu-id="c4816-122">How to: Instantiate a TimeZoneInfo object</span></span>](../../../docs/standard/datetime/instantiate-time-zone-info.md)

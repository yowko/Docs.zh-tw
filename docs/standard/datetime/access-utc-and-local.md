---
title: 如何： 存取預先定義的 UTC 與本地時間區域物件
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
ms.openlocfilehash: b7ddf7ba69d8bed84f62d329fd26794e2641d954
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571143"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="e9381-102">如何： 存取預先定義的 UTC 與本地時間區域物件</span><span class="sxs-lookup"><span data-stu-id="e9381-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="e9381-103"><xref:System.TimeZoneInfo>類別提供兩個屬性：<xref:System.TimeZoneInfo.Utc%2A>和<xref:System.TimeZoneInfo.Local%2A>，，讓您的程式碼存取預先定義的時區物件。</span><span class="sxs-lookup"><span data-stu-id="e9381-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="e9381-104">本主題討論如何存取這些屬性所傳回的 <xref:System.TimeZoneInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="e9381-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="e9381-105">存取國際標準時間 (UTC) TimeZoneInfo 物件</span><span class="sxs-lookup"><span data-stu-id="e9381-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="e9381-106">使用`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性來存取國際標準時間。</span><span class="sxs-lookup"><span data-stu-id="e9381-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="e9381-107">與其指派<xref:System.TimeZoneInfo>物件屬性所傳回的物件變數，以繼續存取透過國際標準時間<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="e9381-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="e9381-108">存取當地時區</span><span class="sxs-lookup"><span data-stu-id="e9381-108">To access the local time zone</span></span>

1. <span data-ttu-id="e9381-109">使用`static`(`Shared`在 Visual Basic 中)<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性來存取本機系統時區。</span><span class="sxs-lookup"><span data-stu-id="e9381-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="e9381-110">與其指派<xref:System.TimeZoneInfo>物件屬性所傳回的物件變數，以繼續存取透過本地時區<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="e9381-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="e9381-111">範例</span><span class="sxs-lookup"><span data-stu-id="e9381-111">Example</span></span>

<span data-ttu-id="e9381-112">下列程式碼會使用 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 和 <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> 屬性轉換美國及加拿大東部標準時區的時間，以及對主控台顯示時區名稱。</span><span class="sxs-lookup"><span data-stu-id="e9381-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="e9381-113">您一定要存取透過本地時區<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>屬性，而不是指定本地時間區域以<xref:System.TimeZoneInfo>物件變數。</span><span class="sxs-lookup"><span data-stu-id="e9381-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="e9381-114">同樣地，您應該一律存取透過國際標準時間<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>至區域的屬性，而非指定 UTC<xref:System.TimeZoneInfo>物件變數。</span><span class="sxs-lookup"><span data-stu-id="e9381-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="e9381-115">這可防止<xref:System.TimeZoneInfo>物件變數，使其免於無效的呼叫所<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="e9381-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="e9381-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e9381-116">Compiling the code</span></span>

<span data-ttu-id="e9381-117">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e9381-117">This example requires:</span></span>

* <span data-ttu-id="e9381-118">對 system.core.dll 的參考無法加入至專案。</span><span class="sxs-lookup"><span data-stu-id="e9381-118">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="e9381-119">確認<xref:System>以匯入命名空間`using`陳述式 （C# 程式碼所需）。</span><span class="sxs-lookup"><span data-stu-id="e9381-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="e9381-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9381-120">See also</span></span>

<span data-ttu-id="e9381-121">[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[尋找本機系統上所定義的時區](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[如何： 具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span><span class="sxs-lookup"><span data-stu-id="e9381-121">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span></span>

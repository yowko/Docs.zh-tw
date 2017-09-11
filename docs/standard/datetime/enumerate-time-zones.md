---
title: "如何：列舉電腦上展示的時區"
description: "如何列舉電腦上展示的時區"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f30ba2a483ff7e5867417969946c2774175d5e3d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="2d3a0-104">如何：列舉電腦上展示的時區</span><span class="sxs-lookup"><span data-stu-id="2d3a0-104">How to: enumerate time zones present on a computer</span></span>

<span data-ttu-id="2d3a0-105">若要順利處理指定的時區，需要可供系統使用之時區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-105">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="2d3a0-106">例如，Windows 作業系統會將此資訊儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-106">For example, the Windows operating system stores this information in the registry.</span></span> <span data-ttu-id="2d3a0-107">不過，雖然全世界的時區總數很大，但是登錄只會包含其中一部分的資訊。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-107">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="2d3a0-108">此外，登錄本身是內容很容易變成故意或意外變更的動態結構。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-108">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="2d3a0-109">因此，應用程式無法永遠假設特定時區已定義且可在系統上使用。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-109">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="2d3a0-110">許多使用時區資訊應用程式之應用程式的第一個步驟，為是否可在本機系統上使用必要時區，或將可從中選取的時區清單提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-110">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="2d3a0-111">這需要應用程式列舉本機系統上所定義的時區。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-111">This requires that an application enumerate the time zones defined on a local system.</span></span> 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="2d3a0-112">列舉本機系統上展示的時區</span><span class="sxs-lookup"><span data-stu-id="2d3a0-112">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="2d3a0-113">呼叫 [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) 方法。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-113">Call the [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) method.</span></span> <span data-ttu-id="2d3a0-114">這個方法會傳回 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件的泛型 [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) 集合。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-114">The method returns a generic [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects.</span></span> <span data-ttu-id="2d3a0-115">集合中的項目會根據 [DisplayName](xref:System.TimeZoneInfo.DisplayName) 屬性進行排序。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-115">The entries in the collection are sorted by their [DisplayName](xref:System.TimeZoneInfo.DisplayName) property.</span></span> <span data-ttu-id="2d3a0-116">例如: </span><span class="sxs-lookup"><span data-stu-id="2d3a0-116">For example:</span></span>

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. <span data-ttu-id="2d3a0-117">使用 `foreach` 迴圈 (在 C# 中) 或 `For Each…Next` 迴圈 (在 Visual Basic 中) 來列舉集合中的個別 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，並對每個物件執行任何必要的處理。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-117">Enumerate the individual [TimeZoneInfo](xref:System.TimeZoneInfo) objects in the collection by using a `foreach` loop (in C#) or a `For Each…Next` loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="2d3a0-118">例如，下列程式碼會列舉步驟 1 中所傳回之 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件的 [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) 集合，並在主控台上列出每個時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="2d3a0-118">For example, the following code enumerates the [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) collection of [TimeZoneInfo](xref:System.TimeZoneInfo) objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a><span data-ttu-id="2d3a0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d3a0-119">See Also</span></span>

[<span data-ttu-id="2d3a0-120">日期、時間及時區</span><span class="sxs-lookup"><span data-stu-id="2d3a0-120">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="2d3a0-121">尋找本機系統上定義的時區</span><span class="sxs-lookup"><span data-stu-id="2d3a0-121">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)



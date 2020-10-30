---
title: 作法：列舉電腦上既有的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], enumerating
- enumerating time zones [.NET]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: a51e9d0c51968d57e0d79dd80d8619ab11cdbf93
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063764"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="c495e-102">作法：列舉電腦上既有的時區</span><span class="sxs-lookup"><span data-stu-id="c495e-102">How to: Enumerate time zones present on a computer</span></span>

<span data-ttu-id="c495e-103">若要順利處理指定的時區，需要可供系統使用之時區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c495e-103">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="c495e-104">Windows XP 和 Windows Vista 作業系統會將這項資訊儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="c495e-104">The Windows XP and Windows Vista operating systems store this information in the registry.</span></span> <span data-ttu-id="c495e-105">不過，雖然全世界的時區總數很大，但是登錄只會包含其中一部分的資訊。</span><span class="sxs-lookup"><span data-stu-id="c495e-105">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="c495e-106">此外，登錄本身是內容很容易變成故意或意外變更的動態結構。</span><span class="sxs-lookup"><span data-stu-id="c495e-106">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="c495e-107">因此，應用程式無法永遠假設特定時區已定義且可在系統上使用。</span><span class="sxs-lookup"><span data-stu-id="c495e-107">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="c495e-108">許多使用時區資訊應用程式之應用程式的第一個步驟，為是否可在本機系統上使用必要時區，或將可從中選取的時區清單提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="c495e-108">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="c495e-109">這需要應用程式列舉本機系統上所定義的時區。</span><span class="sxs-lookup"><span data-stu-id="c495e-109">This requires that an application enumerate the time zones defined on a local system.</span></span>

> [!NOTE]
> <span data-ttu-id="c495e-110">如果應用程式依賴可能無法在本機系統上定義的特定時區，應用程式可以將時區的相關資訊序列化和還原序列化，以確保其存在。</span><span class="sxs-lookup"><span data-stu-id="c495e-110">If an application relies on the presence of a particular time zone that may not be defined on a local system, the application can ensure its presence by serializing and deserializing information about the time zone.</span></span> <span data-ttu-id="c495e-111">然後，您可以將時區新增至清單控制項，讓應用程式使用者可以選取它。</span><span class="sxs-lookup"><span data-stu-id="c495e-111">The time zone can then be added to a list control so that the application user can select it.</span></span> <span data-ttu-id="c495e-112">如需詳細資訊，請參閱 [如何：將時區儲存到內嵌資源](save-time-zones-to-an-embedded-resource.md) 和 [如何：從內嵌資源還原時區](restore-time-zones-from-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="c495e-112">For details, see [How to: Save Time Zones to an Embedded Resource](save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](restore-time-zones-from-an-embedded-resource.md).</span></span>

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="c495e-113">列舉本機系統上展示的時區</span><span class="sxs-lookup"><span data-stu-id="c495e-113">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="c495e-114">呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c495e-114">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c495e-115">方法會傳回物件的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合 <xref:System.TimeZoneInfo> 。</span><span class="sxs-lookup"><span data-stu-id="c495e-115">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span> <span data-ttu-id="c495e-116">集合中的專案會依其屬性排序 <xref:System.TimeZoneInfo.DisplayName%2A> 。</span><span class="sxs-lookup"><span data-stu-id="c495e-116">The entries in the collection are sorted by their <xref:System.TimeZoneInfo.DisplayName%2A> property.</span></span> <span data-ttu-id="c495e-117">例如：</span><span class="sxs-lookup"><span data-stu-id="c495e-117">For example:</span></span>

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. <span data-ttu-id="c495e-118"><xref:System.TimeZoneInfo>使用 c # 中的迴圈 (來列舉集合中的個別物件 `foreach` ) 或 ... `For Each``Next`</span><span class="sxs-lookup"><span data-stu-id="c495e-118">Enumerate the individual <xref:System.TimeZoneInfo> objects in the collection by using a `foreach` loop (in C#) or a `For Each`…`Next`</span></span> <span data-ttu-id="c495e-119">迴圈 (Visual Basic) ，並在每個物件上執行任何必要的處理。</span><span class="sxs-lookup"><span data-stu-id="c495e-119">loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="c495e-120">例如，下列程式碼會列舉 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.TimeZoneInfo> 步驟1中傳回的物件集合，並列出主控台上每個時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="c495e-120">For example, the following code enumerates the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a><span data-ttu-id="c495e-121">向使用者顯示本機系統上的時區清單</span><span class="sxs-lookup"><span data-stu-id="c495e-121">To present the user with a list of time zones present on the local system</span></span>

1. <span data-ttu-id="c495e-122">呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c495e-122">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c495e-123">方法會傳回物件的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合 <xref:System.TimeZoneInfo> 。</span><span class="sxs-lookup"><span data-stu-id="c495e-123">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span>

2. <span data-ttu-id="c495e-124">將步驟1中傳回的集合指派給 `DataSource` Windows forms 或 ASP.NET 清單控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="c495e-124">Assign the collection returned in step 1 to the `DataSource` property of a Windows forms or ASP.NET list control.</span></span>

3. <span data-ttu-id="c495e-125">取出 <xref:System.TimeZoneInfo> 使用者已選取的物件。</span><span class="sxs-lookup"><span data-stu-id="c495e-125">Retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span>

<span data-ttu-id="c495e-126">此範例提供 Windows 應用程式的圖例。</span><span class="sxs-lookup"><span data-stu-id="c495e-126">The example provides an illustration for a Windows application.</span></span>

## <a name="example"></a><span data-ttu-id="c495e-127">範例</span><span class="sxs-lookup"><span data-stu-id="c495e-127">Example</span></span>

<span data-ttu-id="c495e-128">此範例會啟動 Windows 應用程式，以在清單方塊中顯示系統上定義的時區。</span><span class="sxs-lookup"><span data-stu-id="c495e-128">The example starts a Windows application that displays the time zones defined on a system in a list box.</span></span> <span data-ttu-id="c495e-129">然後，此範例會顯示一個對話方塊，其中包含 <xref:System.TimeZoneInfo.DisplayName%2A> 使用者所選取之時區物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="c495e-129">The example then displays a dialog box that contains the value of the <xref:System.TimeZoneInfo.DisplayName%2A> property of the time zone object selected by the user.</span></span>

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

<span data-ttu-id="c495e-130">大部分的清單控制項 (例如 <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> 或 <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> 控制項) 可讓您將物件變數集合指派給其屬性，只要 `DataSource` 該集合會實作為介面即可 <xref:System.Collections.IEnumerable> 。</span><span class="sxs-lookup"><span data-stu-id="c495e-130">Most list controls (such as the <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> or <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> control) allow you to assign a collection of object variables to their `DataSource` property as long as that collection implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="c495e-131"> (泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 類別會執行這項工作。 ) 若要在集合中顯示個別物件，控制項會呼叫該物件的 `ToString` 方法，以解壓縮用來表示物件的字串。</span><span class="sxs-lookup"><span data-stu-id="c495e-131">(The generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class does this.) To display an individual object in the collection, the control calls that object's `ToString` method to extract the string that is used to represent the object.</span></span> <span data-ttu-id="c495e-132">在物件的情況下 <xref:System.TimeZoneInfo> ，方法會傳回 `ToString` 物件的 <xref:System.TimeZoneInfo> 顯示名稱 (其屬性的值 <xref:System.TimeZoneInfo.DisplayName%2A>) 。</span><span class="sxs-lookup"><span data-stu-id="c495e-132">In the case of <xref:System.TimeZoneInfo> objects, the `ToString` method returns the <xref:System.TimeZoneInfo> object's display name (the value of its <xref:System.TimeZoneInfo.DisplayName%2A> property).</span></span>

> [!NOTE]
> <span data-ttu-id="c495e-133">由於清單控制項會呼叫物件的 `ToString` 方法，因此您可以將物件集合指派 <xref:System.TimeZoneInfo> 給控制項、讓控制項顯示每個物件的有意義名稱，以及取得 <xref:System.TimeZoneInfo> 使用者選取的物件。</span><span class="sxs-lookup"><span data-stu-id="c495e-133">Because list controls call an object's `ToString` method, you can assign a collection of <xref:System.TimeZoneInfo> objects to the control, have the control display a meaningful name for each object, and retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span> <span data-ttu-id="c495e-134">這樣就不需要針對集合中的每個物件解壓縮字串，而是將字串指派給集合，然後再指派給控制項的 `DataSource` 屬性，取出使用者已選取的字串，然後使用這個字串來解壓縮其所描述的物件。</span><span class="sxs-lookup"><span data-stu-id="c495e-134">This eliminates the need to extract a string for each object in the collection, assign the string to a collection that is in turn assigned to the control's `DataSource` property, retrieve the string the user has selected, and then use this string to extract the object that it describes.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="c495e-135">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="c495e-135">Compiling the code</span></span>

<span data-ttu-id="c495e-136">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="c495e-136">This example requires:</span></span>

- <span data-ttu-id="c495e-137">匯入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="c495e-137">That the following namespaces be imported:</span></span>

  <span data-ttu-id="c495e-138"><xref:System> C # 程式碼中的 () </span><span class="sxs-lookup"><span data-stu-id="c495e-138"><xref:System> (in C# code)</span></span>

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a><span data-ttu-id="c495e-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c495e-139">See also</span></span>

- [<span data-ttu-id="c495e-140">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="c495e-140">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="c495e-141">如何：將時區儲存到內嵌資源</span><span class="sxs-lookup"><span data-stu-id="c495e-141">How to: Save time zones to an embedded resource</span></span>](save-time-zones-to-an-embedded-resource.md)
- [<span data-ttu-id="c495e-142">如何：從內嵌資源還原時區</span><span class="sxs-lookup"><span data-stu-id="c495e-142">How to: Restore time zones from an embedded resource</span></span>](restore-time-zones-from-an-embedded-resource.md)

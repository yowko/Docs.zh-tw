---
title: HOW TO：列舉電腦上展示的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 697cd40482aee73fd150359acb710ffc258c3df2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518406"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a><span data-ttu-id="86677-102">HOW TO：列舉電腦上展示的時區</span><span class="sxs-lookup"><span data-stu-id="86677-102">How to: Enumerate time zones present on a computer</span></span>

<span data-ttu-id="86677-103">若要順利處理指定的時區，需要可供系統使用之時區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="86677-103">Successfully working with a designated time zone requires that information about that time zone be available to the system.</span></span> <span data-ttu-id="86677-104">Windows XP 和 Windows Vista 作業系統會將此資訊儲存在登錄中。</span><span class="sxs-lookup"><span data-stu-id="86677-104">The Windows XP and Windows Vista operating systems store this information in the registry.</span></span> <span data-ttu-id="86677-105">不過，雖然全世界的時區總數很大，但是登錄只會包含其中一部分的資訊。</span><span class="sxs-lookup"><span data-stu-id="86677-105">However, although the total number of time zones that exist throughout the world is large, the registry contains information about only a subset of them.</span></span> <span data-ttu-id="86677-106">此外，登錄本身是內容很容易變成故意或意外變更的動態結構。</span><span class="sxs-lookup"><span data-stu-id="86677-106">In addition, the registry itself is a dynamic structure whose contents are subject to both deliberate and accidental change.</span></span> <span data-ttu-id="86677-107">因此，應用程式無法永遠假設特定時區已定義且可在系統上使用。</span><span class="sxs-lookup"><span data-stu-id="86677-107">As a result, an application cannot always assume that a particular time zone is defined and available on a system.</span></span> <span data-ttu-id="86677-108">許多使用時區資訊應用程式之應用程式的第一個步驟，為是否可在本機系統上使用必要時區，或將可從中選取的時區清單提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="86677-108">The first step for many applications that use time zone information applications is to determine whether required time zones are available on the local system, or to give the user a list of time zones from which to select.</span></span> <span data-ttu-id="86677-109">這需要應用程式列舉本機系統上所定義的時區。</span><span class="sxs-lookup"><span data-stu-id="86677-109">This requires that an application enumerate the time zones defined on a local system.</span></span>

> [!NOTE]
> <span data-ttu-id="86677-110">如果應用程式依賴本機系統可能沒有定義為特定時區的目前狀態，應用程式可以確保其目前狀態序列化和還原序列化的相關時區資訊。</span><span class="sxs-lookup"><span data-stu-id="86677-110">If an application relies on the presence of a particular time zone that may not be defined on a local system, the application can ensure its presence by serializing and deserializing information about the time zone.</span></span> <span data-ttu-id="86677-111">時區然後新增到清單控制項，使應用程式使用者可以選取它。</span><span class="sxs-lookup"><span data-stu-id="86677-111">The time zone can then be added to a list control so that the application user can select it.</span></span> <span data-ttu-id="86677-112">如需詳細資訊，請參閱[How to:將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to:從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。</span><span class="sxs-lookup"><span data-stu-id="86677-112">For details, see [How to: Save Time Zones to an Embedded Resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).</span></span>

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a><span data-ttu-id="86677-113">列舉本機系統上展示的時區</span><span class="sxs-lookup"><span data-stu-id="86677-113">To enumerate the time zones present on the local system</span></span>

1. <span data-ttu-id="86677-114">呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="86677-114">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="86677-115">此方法會傳回泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的集合<xref:System.TimeZoneInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="86677-115">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span> <span data-ttu-id="86677-116">集合中的項目會依其<xref:System.TimeZoneInfo.DisplayName%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="86677-116">The entries in the collection are sorted by their <xref:System.TimeZoneInfo.DisplayName%2A> property.</span></span> <span data-ttu-id="86677-117">例如: </span><span class="sxs-lookup"><span data-stu-id="86677-117">For example:</span></span>

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. <span data-ttu-id="86677-118">列舉個別<xref:System.TimeZoneInfo>使用集合中的物件`foreach`迴圈 （在 C#) 或`For Each`...`Next`</span><span class="sxs-lookup"><span data-stu-id="86677-118">Enumerate the individual <xref:System.TimeZoneInfo> objects in the collection by using a `foreach` loop (in C#) or a `For Each`…`Next`</span></span> <span data-ttu-id="86677-119">迴圈 （在 Visual Basic 中)，並在每個物件上執行任何必要的處理。</span><span class="sxs-lookup"><span data-stu-id="86677-119">loop (in Visual Basic), and perform any necessary processing on each object.</span></span> <span data-ttu-id="86677-120">例如，下列程式碼會列舉<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的集合<xref:System.TimeZoneInfo>物件傳回在步驟 1，並列出在主控台上的每個時區的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="86677-120">For example, the following code enumerates the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects returned in step 1 and lists the display name of each time zone on the console.</span></span>

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a><span data-ttu-id="86677-121">若要顯示給使用者的本機系統上展示的時區清單</span><span class="sxs-lookup"><span data-stu-id="86677-121">To present the user with a list of time zones present on the local system</span></span>

1. <span data-ttu-id="86677-122">呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="86677-122">Call the <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="86677-123">此方法會傳回泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的集合<xref:System.TimeZoneInfo>物件。</span><span class="sxs-lookup"><span data-stu-id="86677-123">The method returns a generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection of <xref:System.TimeZoneInfo> objects.</span></span>

2. <span data-ttu-id="86677-124">將指定在步驟 1 中傳回的集合`DataSource`屬性的 Windows form 或 ASP.NET 清單控制項。</span><span class="sxs-lookup"><span data-stu-id="86677-124">Assign the collection returned in step 1 to the `DataSource` property of a Windows forms or ASP.NET list control.</span></span>

3. <span data-ttu-id="86677-125">擷取<xref:System.TimeZoneInfo>使用者選取的物件。</span><span class="sxs-lookup"><span data-stu-id="86677-125">Retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span>

<span data-ttu-id="86677-126">此範例說明針對 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="86677-126">The example provides an illustration for a Windows application.</span></span>

## <a name="example"></a><span data-ttu-id="86677-127">範例</span><span class="sxs-lookup"><span data-stu-id="86677-127">Example</span></span>

<span data-ttu-id="86677-128">此範例會啟動 Windows 應用程式會顯示在清單方塊中的系統上所定義的時區。</span><span class="sxs-lookup"><span data-stu-id="86677-128">The example starts a Windows application that displays the time zones defined on a system in a list box.</span></span> <span data-ttu-id="86677-129">此範例接著會顯示對話方塊，其中包含的值<xref:System.TimeZoneInfo.DisplayName%2A>使用者所選取的時區物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="86677-129">The example then displays a dialog box that contains the value of the <xref:System.TimeZoneInfo.DisplayName%2A> property of the time zone object selected by the user.</span></span>

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

<span data-ttu-id="86677-130">最清單控制項 (例如<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType>或<xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType>控制項) 可讓您指派至的物件變數的集合及其`DataSource`屬性，只要該集合會實作<xref:System.Collections.IEnumerable>介面。</span><span class="sxs-lookup"><span data-stu-id="86677-130">Most list controls (such as the <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> or <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> control) allow you to assign a collection of object variables to their `DataSource` property as long as that collection implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="86677-131">(泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>類別的做法。)若要顯示的個別物件在集合中，控制項會呼叫該物件的`ToString`方法來擷取用來代表物件的字串。</span><span class="sxs-lookup"><span data-stu-id="86677-131">(The generic <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class does this.) To display an individual object in the collection, the control calls that object's `ToString` method to extract the string that is used to represent the object.</span></span> <span data-ttu-id="86677-132">若是<xref:System.TimeZoneInfo>物件，`ToString`方法會傳回<xref:System.TimeZoneInfo>物件的顯示名稱 (的值及其<xref:System.TimeZoneInfo.DisplayName%2A>屬性)。</span><span class="sxs-lookup"><span data-stu-id="86677-132">In the case of <xref:System.TimeZoneInfo> objects, the `ToString` method returns the <xref:System.TimeZoneInfo> object's display name (the value of its <xref:System.TimeZoneInfo.DisplayName%2A> property).</span></span>

> [!NOTE]
> <span data-ttu-id="86677-133">因為清單控制項呼叫的物件`ToString`方法中，您可以將指派的集合<xref:System.TimeZoneInfo>物件來控制，讓控制項顯示有意義的名稱，每一個物件，並擷取<xref:System.TimeZoneInfo>使用者選取的物件。</span><span class="sxs-lookup"><span data-stu-id="86677-133">Because list controls call an object's `ToString` method, you can assign a collection of <xref:System.TimeZoneInfo> objects to the control, have the control display a meaningful name for each object, and retrieve the <xref:System.TimeZoneInfo> object that the user has selected.</span></span> <span data-ttu-id="86677-134">這就不需要擷取集合中每個物件的字串，將字串指派給集合，其中依序指派給控制項的`DataSource`屬性，擷取使用者已選取的字串，然後使用此字串擷取物件它描述。</span><span class="sxs-lookup"><span data-stu-id="86677-134">This eliminates the need to extract a string for each object in the collection, assign the string to a collection that is in turn assigned to the control's `DataSource` property, retrieve the string the user has selected, and then use this string to extract the object that it describes.</span></span> 

## <a name="compiling-the-code"></a><span data-ttu-id="86677-135">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="86677-135">Compiling the code</span></span>

<span data-ttu-id="86677-136">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="86677-136">This example requires:</span></span>

* <span data-ttu-id="86677-137">對 System.Core.dll 的參考加入至專案。</span><span class="sxs-lookup"><span data-stu-id="86677-137">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="86677-138">下列命名空間會匯入：</span><span class="sxs-lookup"><span data-stu-id="86677-138">That the following namespaces be imported:</span></span>

  <span data-ttu-id="86677-139"><xref:System> （在 C# 程式碼）</span><span class="sxs-lookup"><span data-stu-id="86677-139"><xref:System> (in C# code)</span></span>

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a><span data-ttu-id="86677-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86677-140">See also</span></span>

- [<span data-ttu-id="86677-141">日期、時間和時區</span><span class="sxs-lookup"><span data-stu-id="86677-141">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
- [<span data-ttu-id="86677-142">如何：將時區儲存到內嵌資源</span><span class="sxs-lookup"><span data-stu-id="86677-142">How to: Save time zones to an embedded resource</span></span>](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [<span data-ttu-id="86677-143">如何：從內嵌資源還原時區</span><span class="sxs-lookup"><span data-stu-id="86677-143">How to: Restore time zones from an embedded resource</span></span>](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)

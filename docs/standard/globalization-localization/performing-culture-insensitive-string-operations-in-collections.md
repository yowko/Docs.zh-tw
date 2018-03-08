---
title: "在集合中執行不區分文化特性的字串作業"
ms.custom: 
ms.date: 03/30/2017
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
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b84f25aa2470104be98b9f3858091c44f40ba6a7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="8d6fb-102">在集合中執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="8d6fb-102">Performing Culture-Insensitive String Operations in Collections</span></span>
<span data-ttu-id="8d6fb-103"><xref:System.Collections> 命名空間中有某些類別和成員依預設會提供區分文化特性的行為。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="8d6fb-104"><xref:System.Collections.CaseInsensitiveComparer> 和 <xref:System.Collections.CaseInsensitiveHashCodeProvider> 類別的預設建構函式會使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 屬性，初始化新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-104">The default constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8d6fb-105"><xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> 方法的所有多載預設都會使用 `Thread.CurrentCulture` 屬性，建立 <xref:System.Collections.Hashtable> 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="8d6fb-106"><xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> 方法的多載預設會使用 `Thread.CurrentCulture` 來執行區分文化特性的排序。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="8d6fb-107">當字串當作索引鍵使用時，<xref:System.Collections.SortedList> 中的排序和查閱作業可能會受到 `Thread.CurrentCulture` 的影響。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="8d6fb-108">請遵循本節提供的使用建議，以從 `Collections` 命名空間中的這些類別和方法取得不區分文化特性的結果。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>  
  
 <span data-ttu-id="8d6fb-109">**注意：**將 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 傳遞給比較方法的確會執行不區分文化特性的比較。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-109">**Note** Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="8d6fb-110">不過，它不會讓某些項目進行非語言比較，例如檔案路徑、登錄機碼和環境變數。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="8d6fb-111">它也不支援根據比較結果所做出的安全性決策。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="8d6fb-112">若要進行非語言比較或需要支援根據結果的安全性決策，應用程式應該使用可接受 <xref:System.StringComparison> 值的比較方法。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="8d6fb-113">接著，應用程式應該會傳遞 <xref:System.StringComparison>。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-113">The application should then pass <xref:System.StringComparison>.</span></span>  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="8d6fb-114">使用 CaseInsensitiveComparer 和 CaseInsensitiveHashCodeProvider 類別</span><span class="sxs-lookup"><span data-stu-id="8d6fb-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>  
 <span data-ttu-id="8d6fb-115">`CaseInsensitiveHashCodeProvider` 和 `CaseInsensitiveComparer` 的預設建構函式會使用 `Thread.CurrentCulture` 來初始化類別的新執行個體，而產生區分文化特性的行為。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-115">The default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="8d6fb-116">下列程式碼範例所示範的 `Hashtable` 建構函式會區分文化特性，因為它使用 `CaseInsensitiveHashCodeProvider` 和 `CaseInsensitiveComparer` 的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 <span data-ttu-id="8d6fb-117">如果您想要使用 `CaseInsensitiveComparer` 和 `CaseInsensitiveHashCodeProvider` 類別建立不區分文化特性的 `Hashtable`，請使用可接受 `culture` 參數的建構函式初始化這些類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="8d6fb-118">至於 `culture` 參數，請指定 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8d6fb-119">下列程式碼範例會示範不區分文化特性之 `Hashtable` 的建構函式。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="8d6fb-120">使用 CollectionsUtil.CreateCaseInsensitiveHashTable 方法</span><span class="sxs-lookup"><span data-stu-id="8d6fb-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>  
 <span data-ttu-id="8d6fb-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` 方法是很實用的捷徑，可用來建立 `Hashtable` 類別的新執行個體，而此類別會忽略字串的大小寫。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="8d6fb-122">不過，`CollectionsUtil.CreateCaseInsensitiveHashTable` 方法的所有多載會區分文化特性，因為它們使用 `Thread.CurrentCulture` 屬性。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="8d6fb-123">您無法使用此方法來建立不區分文化特性的 `Hashtable`。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="8d6fb-124">若要建立不區分文化特性的 `Hashtable`，請使用可接受 `culture` 參數的 `Hashtable` 建構函式。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="8d6fb-125">至於 `culture` 參數，請指定 `CultureInfo.InvariantCulture`。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="8d6fb-126">下列程式碼範例會示範不區分文化特性之 `Hashtable` 的建構函式。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>   
## <a name="using-the-sortedlist-class"></a><span data-ttu-id="8d6fb-127">使用 SortedList 類別</span><span class="sxs-lookup"><span data-stu-id="8d6fb-127">Using the SortedList Class</span></span>  
 <span data-ttu-id="8d6fb-128">`SortedList` 表示索引鍵/值組的集合，這個集合按索引鍵排序，而且可以按索引鍵和索引存取。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="8d6fb-129">當您使用字串是索引鍵的 `SortedList` 時，排序和查閱作業可能會受到 `Thread.CurrentCulture` 屬性的影響。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="8d6fb-130">若要從 `SortedList` 取得不區分文化特性的行為，請使用其中一個可接受 `comparer` 參數的建構函式來建立 `SortedList`。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="8d6fb-131">`comparer` 參數會指定要在比較索引鍵時使用的 <xref:System.Collections.IComparer> 實作。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="8d6fb-132">至於參數，請指定自訂比較子類別，以使用 `CultureInfo.InvariantCulture` 來比較索引鍵。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="8d6fb-133">下列範例說明不區分文化特性的自訂比較子類別，您可以將此類別指定為 `SortedList` 建構函式的 `comparer` 參數。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>  
  
```vb  
Imports System  
Imports System.Collections  
Imports System.Globalization  
  
Friend Class InvariantComparer  
    Implements IComparer   
    Private m_compareInfo As CompareInfo  
    Friend Shared [Default] As New InvariantComparer()  
  
    Friend Sub New()  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo  
    End Sub     
  
    Public Function Compare(a As Object, b As Object) As Integer _  
            Implements IComparer.Compare  
        Dim sa As String = CType(a, String)  
        Dim sb As String = CType(b, String)  
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then  
            Return m_compareInfo.Compare(sa, sb)  
        Else  
            Return Comparer.Default.Compare(a, b)  
        End If  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Globalization;  
  
internal class InvariantComparer : IComparer   
{  
    private CompareInfo m_compareInfo;  
    internal static readonly InvariantComparer Default = new  
        InvariantComparer();  
  
    internal InvariantComparer()   
    {  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;  
    }  
  
    public int Compare(Object a, Object b)  
    {  
        String sa = a as String;  
        String sb = b as String;  
        if (sa != null && sb != null)  
            return m_compareInfo.Compare(sa, sb);  
        else  
            return Comparer.Default.Compare(a,b);  
    }  
}  
```  
  
 <span data-ttu-id="8d6fb-134">一般而言，如果您對字串使用 `SortedList` 卻沒有指定自訂的非變異值比較子，則在清單填入內容之後，若 `Thread.CurrentCulture` 有所變更，該清單可能會失效。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>  
  
## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="8d6fb-135">使用 ArrayList.Sort 方法</span><span class="sxs-lookup"><span data-stu-id="8d6fb-135">Using the ArrayList.Sort Method</span></span>  
 <span data-ttu-id="8d6fb-136">`ArrayList.Sort` 方法的多載預設會使用 `Thread.CurrentCulture` 屬性來執行區分文化特性的排序。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="8d6fb-137">由於排序次序不同，結果會因文化特性而異。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="8d6fb-138">若要消除區分文化特性的行為，請使用此方法中可接受 `IComparer` 實作的多載。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="8d6fb-139">至於 `comparer` 參數，請指定自訂的非變異值比較子類別，以使用 `CultureInfo.InvariantCulture`。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="8d6fb-140">[使用 SortedList 類別](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)主題會提供自訂非變異值比較子類別的範例。</span><span class="sxs-lookup"><span data-stu-id="8d6fb-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6fb-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d6fb-141">See Also</span></span>  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="8d6fb-142">執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="8d6fb-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>

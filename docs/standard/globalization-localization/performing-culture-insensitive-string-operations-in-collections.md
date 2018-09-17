---
title: 在集合中執行不區分文化特性的字串作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e458f45fea8e2207ced930daebf10e653901fa7
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649194"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>在集合中執行不區分文化特性的字串作業
<xref:System.Collections> 命名空間中有某些類別和成員依預設會提供區分文化特性的行為。 <xref:System.Collections.CaseInsensitiveComparer> 和 <xref:System.Collections.CaseInsensitiveHashCodeProvider> 類別的預設建構函式會使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 屬性，初始化新的執行個體。 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> 方法的所有多載預設都會使用 `Thread.CurrentCulture` 屬性，建立 <xref:System.Collections.Hashtable> 類別的新執行個體。 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> 方法的多載預設會使用 `Thread.CurrentCulture` 來執行區分文化特性的排序。 當字串當作索引鍵使用時，<xref:System.Collections.SortedList> 中的排序和查閱作業可能會受到 `Thread.CurrentCulture` 的影響。 請遵循本節提供的使用建議，以從 `Collections` 命名空間中的這些類別和方法取得不區分文化特性的結果。  
  
 **注意：** 將 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 傳遞給比較方法的確會執行不區分文化特性的比較。 不過，它不會讓某些項目進行非語言比較，例如檔案路徑、登錄機碼和環境變數。 它也不支援根據比較結果所做出的安全性決策。 若要進行非語言比較或需要支援根據結果的安全性決策，應用程式應該使用可接受 <xref:System.StringComparison> 值的比較方法。 接著，應用程式應該會傳遞 <xref:System.StringComparison>。  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>使用 CaseInsensitiveComparer 和 CaseInsensitiveHashCodeProvider 類別  
 `CaseInsensitiveHashCodeProvider` 和 `CaseInsensitiveComparer` 的預設建構函式會使用 `Thread.CurrentCulture` 來初始化類別的新執行個體，而產生區分文化特性的行為。 下列程式碼範例所示範的 `Hashtable` 建構函式會區分文化特性，因為它使用 `CaseInsensitiveHashCodeProvider` 和 `CaseInsensitiveComparer` 的預設建構函式。  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 如果您想要使用 `CaseInsensitiveComparer` 和 `CaseInsensitiveHashCodeProvider` 類別建立不區分文化特性的 `Hashtable`，請使用可接受 `culture` 參數的建構函式初始化這些類別的新執行個體。 至於 `culture` 參數，請指定 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。 下列程式碼範例會示範不區分文化特性之 `Hashtable` 的建構函式。  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>使用 CollectionsUtil.CreateCaseInsensitiveHashTable 方法  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` 方法是很實用的捷徑，可用來建立 `Hashtable` 類別的新執行個體，而此類別會忽略字串的大小寫。 不過，`CollectionsUtil.CreateCaseInsensitiveHashTable` 方法的所有多載會區分文化特性，因為它們使用 `Thread.CurrentCulture` 屬性。 您無法使用此方法來建立不區分文化特性的 `Hashtable`。 若要建立不區分文化特性的 `Hashtable`，請使用可接受 `culture` 參數的 `Hashtable` 建構函式。 至於 `culture` 參數，請指定 `CultureInfo.InvariantCulture`。 下列程式碼範例會示範不區分文化特性之 `Hashtable` 的建構函式。  
  
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
## <a name="using-the-sortedlist-class"></a>使用 SortedList 類別  
 `SortedList` 表示索引鍵/值組的集合，這個集合按索引鍵排序，而且可以按索引鍵和索引存取。 當您使用字串是索引鍵的 `SortedList` 時，排序和查閱作業可能會受到 `Thread.CurrentCulture` 屬性的影響。 若要從 `SortedList` 取得不區分文化特性的行為，請使用其中一個可接受 `comparer` 參數的建構函式來建立 `SortedList`。 `comparer` 參數會指定要在比較索引鍵時使用的 <xref:System.Collections.IComparer> 實作。 至於參數，請指定自訂比較子類別，以使用 `CultureInfo.InvariantCulture` 來比較索引鍵。 下列範例說明不區分文化特性的自訂比較子類別，您可以將此類別指定為 `SortedList` 建構函式的 `comparer` 參數。  
  
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
  
 一般而言，如果您對字串使用 `SortedList` 卻沒有指定自訂的非變異值比較子，則在清單填入內容之後，若 `Thread.CurrentCulture` 有所變更，該清單可能會失效。  
  
## <a name="using-the-arraylistsort-method"></a>使用 ArrayList.Sort 方法  
 `ArrayList.Sort` 方法的多載預設會使用 `Thread.CurrentCulture` 屬性來執行區分文化特性的排序。 由於排序次序不同，結果會因文化特性而異。 若要消除區分文化特性的行為，請使用此方法中可接受 `IComparer` 實作的多載。 至於 `comparer` 參數，請指定自訂的非變異值比較子類別，以使用 `CultureInfo.InvariantCulture`。 [使用 SortedList 類別](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)主題會提供自訂非變異值比較子類別的範例。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.CaseInsensitiveComparer>  
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
- <xref:System.Collections.SortedList>  
- <xref:System.Collections.Hashtable>  
- <xref:System.Collections.IComparer>  
- [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>

---
title: "在集合中執行不區分文化特性的字串作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ArrayList.Sort 方法"
  - "CaseInsensitiveComparer 類別, 使用"
  - "CaseInsensitiveHashCodeProvider 類別, 使用"
  - "集合 [.NET Framework], 不區分文化特性的字串之作業"
  - "CollectionsUtil.CreateCaseInsensitiveHashtable 方法"
  - "文化特性參數"
  - "不區分文化特性的字串之作業, 集合"
  - "SortedList 類別, 不區分文化特性的字串之作業"
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 在集合中執行不區分文化特性的字串作業
<xref:System.Collections> 命名空間中有類別和成員，預設會提供區分文化特性的行為。  <xref:System.Collections.CaseInsensitiveComparer> 和 <xref:System.Collections.CaseInsensitiveHashCodeProvider> 類別的預設建構函式會使用 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName> 屬性初始化新的執行個體。  [CollectionsUtil.CreateCaseInsensitiveHashTable](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic) 方法的所有多載會在預設情況下使用 `Thread.CurrentCulture` 屬性建立 <xref:System.Collections.Hashtable> 類別的新執行個體。  預設情況下，<xref:System.Collections.ArrayList.Sort%2A?displayProperty=fullName> 方法的多載會使用 `Thread.CurrentCulture` 執行區分文化特性的排序。  若使用字串做為索引鍵，則 <xref:System.Collections.SortedList> 中的排序和查閱會受到 `Thread.CurrentCulture` 所影響。  請遵照本章節中提供的使用建議，從 `Collections` 命名空間的這些類別和方法取得不區分文化特性的結果。  
  
 **注意**：將 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 傳遞給比較方法，的確會執行不區分文化特性的比較。  然而，這並不會進行非語言比較，例如檔案路徑、登錄機碼和環境變數。  同時也不會支援依據比較結果進行的安全性決策。  對於非語言比較或以結果為基礎之安全性決策的支援，應用程式應該使用接受 <xref:System.StringComparison> 值的比較方法。  然後應用程式應該傳遞 <xref:System.StringComparison>。  
  
## 使用 CaseInsensitiveComparer 和 CaseInsensitiveHashCodeProvider 類別  
 `CaseInsensitiveHashCodeProvider` 和 `CaseInsensitiveComparer` 的預設建構函式會使用 `Thread.CurrentCulture` 初始化新的類別執行個體，以產生區分文化特性的行為。  下列程式碼範例所示範之 `Hashtable` 的建構函式會區分文化特性，因為它使用的是 `CaseInsensitiveHashCodeProvider` 和 `CaseInsensitiveComparer` 的預設建構函式。  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 如果您想要使用 `CaseInsensitiveComparer` 和 `CaseInsensitiveHashCodeProvider` 類別建立不區分文化特性的 `Hashtable`，請使用接受 `culture` 參數的建構函式，初始化這些類別的新執行個體。  對於 `culture` 參數，請指定 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。  下列程式碼範例示範不區分文化特性的 `Hashtable` 建構函式。  
  
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
  
## 使用 CollectionsUtil.CreateCaseInsensitiveHashTable 方法  
 在針對會忽略字串大小寫的 `Hashtable` 類別建立新執行個體時，`CollectionsUtil.CreateCaseInsensitiveHashTable` 方法是個實用的簡捷方式。  然而，`CollectionsUtil.CreateCaseInsensitiveHashTable` 方法的所有多載因為使用 `Thread.CurrentCulture` 屬性，所以是會區分文化特性的。  您無法使用這個方法建立不區分文化特性的 `Hashtable`。  若要建立不區分文化特性的 `Hashtable`，請使用接受 `culture` 參數的 `Hashtable` 建構函式。  對於 `culture` 參數，請指定 `CultureInfo.InvariantCulture`。  下列程式碼範例示範不區分文化特性的 `Hashtable` 建構函式。  
  
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
## 使用 SortedList 類別  
 `SortedList` 代表索引鍵值組的集合，其可根據索引鍵排序，並可按照索引鍵和按照索引進行存取。  當您使用其中字串為索引鍵的 `SortedList` 時，排序和查閱會受到 `Thread.CurrentCulture` 屬性的影響。  若要從 `SortedList` 取得不區分文化特性的行為，請使用接受 `comparer` 參數的其中一個建構函式，建立 `SortedList`。  `comparer` 參數會指定在比較索引鍵時所使用的 <xref:System.Collections.IComparer> 實作。  對於參數，請指定會使用 `CultureInfo.InvariantCulture` 的自訂比較子類別，以比較索引鍵。  下列範例示範自訂的不區分文化特性比較子類別，您可以將其指定為 `SortedList` 建構函式的 `comparer` 參數。  
  
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
  
 一般而言，如果您在字串上使用 `SortedList` 卻沒有指定自訂的非變異比較子，在清單已填入後對 `Thread.CurrentCulture` 進行的變更可以使清單失效。  
  
## 使用 ArrayList.Sort 方法  
 預設情況下，`ArrayList.Sort` 方法的多載會使用 `Thread.CurrentCulture` 屬性執行區分文化特性的排序。  因不同排序次序，結果可以因文化特性而有所不同。  若要排除區分文化特性的行為，請使用接受 `IComparer` 實作之這個方法的多載。  對於 `comparer` 參數，請指定會使用 `CultureInfo.InvariantCulture` 的自訂非變異比較子類別。  自訂非變異比較子類別的範例在[使用 SortedList 類別](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)主題中有提供。  
  
## 請參閱  
 <xref:System.Collections.CaseInsensitiveComparer>   
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>   
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=fullName>   
 <xref:System.Collections.SortedList>   
 <xref:System.Collections.Hashtable>   
 <xref:System.Collections.IComparer>   
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)   
 [CollectionsUtil.CreateCaseInsensitiveHashTable 方法](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic)
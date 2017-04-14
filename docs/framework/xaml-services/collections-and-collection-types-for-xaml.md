---
title: "Collections and Collection Types for XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
caps.latest.revision: 2
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 2
---
# Collections and Collection Types for XAML
本主題說明如何定義屬性的型別是用來支援集合，並對產生的集合項目做為項目子系的父物件項目或屬性項目支援 XAML 語法。  
  
## XAML 集合概念  
 就概念而言，任何在 XAML 中，其中有多個子項目範圍內的 XAML 物件項目或 XAML 屬性項目必須實作為集合關聯。  該集合必須是該關聯性中的父系的 XAML 型別特定的 XAML 屬性相關聯。  屬性必須是集合，因為 XAML 處理器預期要指派標記，以支援集合屬性的新加入的項目中的每個項目。  
  
 在 XAML 語言層級的集合支援實際上的需求都沒有完整定義。  集合可以是清單或字典 \(但非兩者\) 的概念定義在 XAML 語言層級中，但所屬的支援型別代表的任一個清單或字典不由 XAML 語言定義。  
  
 在中。NET 架構的 XAML 服務，XAML 集合支援的概念更清楚地定義的角度來看。NET Framework 支援型別。  具體來說，集合的 XAML 支援根據幾個。NET Framework 的概念和 Api 在一般情況下所使用的清單和字典。NET 應用程式。  
  
1.  <xref:System.Collections.IList>介面指示清單集合。  
  
2.  <xref:System.Collections.IDictionary>介面指示 「 dicionary 」 集合。  
  
3.  <xref:System.Array>代表陣列中，且陣列支援<xref:System.Collections.IList>方法。  
  
 在每一個這些集合的概念。NET Framework XAML 服務 XAML 處理器預期會呼叫`Add`的集合屬性的型別以特定執行個體的方法。  或者，您也可以在序列化的案例中，XAML 處理器會產生不連續的 XAML 型別執行個體，每個項目位於清單、 字典或陣列的 「 項目 」 的每個集合的特定概念為基礎。  These are : <xref:System.Collections.IList.Item%2A>;  <xref:System.Collections.IDictionary.Item%2A>; the explicit <xref:System.Array.System%23Collections%23IList%23Item%2A> for <xref:System.Array>.  
  
## 泛型集合  
 泛型集合可能會很有用的將軍。NET 架構的程式設計，也可用於 XAML 集合屬性。  不過，泛型介面<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>不以識別。NET Framework XAML 服務 XAML 處理器為相當於非泛用<xref:System.Collections.IList>或<xref:System.Collections.IDictionary>。  建議的方法的泛型集合屬性型別是衍生自類別而不是實作的介面， <xref:System.Collections.Generic.List%601>或<xref:System.Collections.Generic.Dictionary%602>。  這些類別會實作非泛型介面，並因此納入基底實作中的 XAML 集合預期的支援。  
  
## 唯讀集合，並初始化邏輯  
 在中。NET Framework 程式設計中，很常見的設計模式，以便存放值，以集合為唯讀的集合中的任何屬性。  這種模式可讓擁有較佳的控制項集合會受到什麼影響之集合屬性的執行個體。.  明確地說，此模式會防止意外取代整個已存在集合中的\] 屬性設定。  在此模式中，任何對呼叫端集合的存取而是應由呼叫方法或屬性，例如只要集合型別和 \(或\) 的相關集合介面支援<xref:System.Collections.IList>。  
  
 使用這種模式時，表示唯讀集合屬性公開 \(expose\) 的任何類別必須先初始化該屬性，以包含空集合。  通常為該類別的建構行為的一部份執行初始化。  很有用，對於 XAML 而言，是很重要這種邏輯會固定參考預設建構函式，因為 XAML 通常會呼叫預設建構函式之前處理內容 \(集合內容或其他方式\)。  
  
## XAML 型別系統支援和集合  
 剖析 XAML 填入與序列化集合屬性的基本機制，超出的 XAML 型別系統，在中實作時。NET Framework XAML 服務包括幾個屬於在 XAML 中集合的設計功能。  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A>傳回值為 true 的 XAML 型別所提供 XAML 集合支援的型別支援。  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A>與<xref:System.Xaml.XamlType.IsArray%2A>可以進一步指定 XAML 型別支援哪一種集合模式。  自訂的 XAML 處理器為基礎。NET Framework XAML 服務與支援 XAML 的型別系統，但不是以現有的<xref:System.Xaml.XamlWriter>的實作，了解哪一種集合模式會使用可能需要知道哪一種方法來叫用的集合處理。  
  
3.  原先的屬性值的每個可能受覆寫的<xref:System.Xaml.XamlType.LookupCollectionKind%2A>的 XAML 型別上。
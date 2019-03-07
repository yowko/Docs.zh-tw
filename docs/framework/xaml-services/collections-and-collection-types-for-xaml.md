---
title: XAML 的集合和集合類型
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 4123b64545f7c47a96c4cae496046a89b7e576b0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494619"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML 的集合和集合類型

本主題描述如何定義旨在支援集合，並做為父物件的項目或屬性項目的項目子系，集合的項目具現化時，對 XAML 語法的類型屬性。

## <a name="xaml-collection-concepts"></a>XAML 集合概念

就概念而言，任何關聯性中，有多個子系的項目範圍內的 XAML 物件項目或 XAML 屬性項目必須實作為一個集合的 XAML。 該集合必須是特定的 XAML 屬性的父系，該關聯性中的 XAML 型別相關聯。 屬性必須是集合，因為 XAML 處理器預期指派標記，以支援集合屬性的新加入項目中的每個項目。

在 XAML 語言層級的集合支援的確切需求未完整定義。 集合可以是其中一種清單或字典 （但不是能兩者同時） 的概念定義在 XAML 語言層級，但哪一個支援型別代表任一清單或字典不由 XAML 語言定義。

在.NET Framework XAML 服務中，XAML 集合支援的概念是以.NET Framework 支援型別更清楚地定義的。 具體來說，集合的 XAML 支援根據幾個用於 list 和 dictionary 在一般的.NET Framework 程式設計的 Api 及.NET Framework 的概念。

1. <xref:System.Collections.IList>介面表示清單集合。

2. <xref:System.Collections.IDictionary>介面表示字典集合。

3. <xref:System.Array> 表示陣列和陣列支援<xref:System.Collections.IList>方法。

在每個這些集合的概念，.NET Framework XAML 服務 XAML 處理器預期呼叫`Add`集合屬性的類型的特定執行個體上的方法。 或者，在序列化案例中，XAML 處理器會產生每個項目清單、 字典或 「 項目 」 的每個集合的特定概念為基礎的陣列中所找到的離散 XAML 型別執行個體。 這些是： <xref:System.Collections.IList.Item%2A>;<xref:System.Collections.IDictionary.Item%2A>; 明確<xref:System.Array.System%23Collections%23IList%23Item%2A>如<xref:System.Array>。

## <a name="generic-collections"></a>泛型集合

泛型集合可用於一般的.NET Framework 程式，並也用於 XAML 集合屬性。 不過，泛型介面<xref:System.Collections.Generic.IList%601>並<xref:System.Collections.Generic.IDictionary%602>不會視為相當於非泛型的.NET Framework XAML 服務 XAML 處理器識別<xref:System.Collections.IList>或<xref:System.Collections.IDictionary>。 而不是實作介面，建議的方法，針對泛型集合屬性類型是衍生自類別<xref:System.Collections.Generic.List%601>或<xref:System.Collections.Generic.Dictionary%602>。 這些類別會實作非泛型介面，並因此包括預期的支援 XAML 集合中的基底實作。

## <a name="read-only-collections-and-initialization-logic"></a>唯讀的集合和初始化邏輯

在.NET Framework 程式設計中，它是常見的設計模式，以使保留的值集合為唯讀集合的任何屬性。 此模式允許的執行個體擁有較佳的控制項集合會發生什麼事集合屬性... 具體而言，模式可防止意外取代整個已經存在的收集設定屬性。 在此模式中，任何集合的存取權由呼叫端應該改為設定成藉由呼叫方法或屬性，因為這類支援集合類型及/或相關集合介面<xref:System.Collections.IList>。

使用此模式表示任何類別會公開唯讀集合的屬性必須先初始化該屬性來保留為空集合。 通常會執行初始化類別的建構行為的一部分。 用於 XAML，它是很重要的預設建構函式，固定參考這類邏輯因為 XAML 通常會呼叫預設建構函式之前處理的屬性 (集合屬性或其他)。

## <a name="xaml-type-system-support-and-collections"></a>XAML 類型系統支援和集合

剖析 XAML 和填入或序列化集合屬性的基本機制，除了在.NET Framework XAML 服務實作的 XAML 類型系統會包含數個設計功能的相關 XAML 中的集合。

1. <xref:System.Xaml.XamlType.IsCollection%2A> 如果支援 XAML 集合的型別所支援的 XAML 型別，傳回 true。

2. <xref:System.Xaml.XamlType.IsDictionary%2A> 和<xref:System.Xaml.XamlType.IsArray%2A>可以進一步指定的 XAML 型別支援的收集模式。 自訂 XAML 處理器為基礎.NET Framework XAML 服務和 XAML 類型系統但不是根據現有的<xref:System.Xaml.XamlWriter>實作中，了解使用的收集模式可能需要才能知道要叫用哪一種方法收集處理程序。

3. 每個先前的屬性值可能會受到覆寫<xref:System.Xaml.XamlType.LookupCollectionKind%2A>XAML 型別上。

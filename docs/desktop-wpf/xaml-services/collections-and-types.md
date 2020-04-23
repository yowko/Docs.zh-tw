---
title: XAML 的集合和集合類型
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 2ec58026c605df31489c8aab4c4cc714dab11474
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "82071294"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML 的收集類型

本文介紹如何定義旨在支援集合的類型的屬性,並支援 XAML 語法,以便將集合項實例化為父物件元素或屬性元素的元素子級。

## <a name="xaml-collection-concepts"></a>XAML 收集概念

從概念上講,XAML 中任何在 XAML 物件元素或 XAML 屬性元素範圍內有多個子項的關係都必須作為集合實現。 該集合必須與 XAML 類型的特定 XAML 屬性相關聯,該屬性是該關係中的父級。 屬性必須是集合,因為 XAML 處理器希望將標記中的每個項分配為備份集合屬性的新添加項。

在 XAML 語言級別,收集支持的確切要求尚未完全定義。 集合可以是清單或字典(但不能同時兩者)的概念在 XAML 語言級別定義,但哪些支援類型表示列表或字典不是由 XAML 語言定義的。

在 .NET XAML 服務中,XAML 集合支援的概念在 .NET 支援類型方面定義得更清晰。 具體來說,XAML 對集合的支援基於幾個 .NET 概念和 API,這些概念和 API 用於一般清單和字典 .NET 程式設計。

1. 介面<xref:System.Collections.IList>指示清單集合。

2. 介面<xref:System.Collections.IDictionary>指示字典集合。

3. <xref:System.Array>表示陣列,陣組支援<xref:System.Collections.IList>方法。

在這些集合概念中,.NET XAML 服務 XAML`Add`處理器期望在集合屬性類型的特定實例上調用 該方法。 或者,在序列化方案中,XAML 處理器根據每個集合的特定概念"Item"為每個在清單、字典或陣列中找到的每個項生成離散的 XAML 類型實例。 這些項目是: <xref:System.Collections.IList.Item%2A?displayProperty=nameWithType><xref:System.Collections.IDictionary.Item%2A?displayProperty=nameWithType>;的顯式<xref:System.Array.System%23Collections%23IList%23Item%2A?displayProperty=nameWithType> <xref:System.Array> 。

## <a name="generic-collections"></a>通用集合

泛型集合可用於常規 .NET 程式設計,也可用於 XAML 集合屬性。 但是,泛型介面<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>.NET XAML 服務 XAML 處理器未識別為<xref:System.Collections.IList>等<xref:System.Collections.IDictionary>效於非泛型或 。 泛型集合屬性類型的推薦方法是從類<xref:System.Collections.Generic.List%601><xref:System.Collections.Generic.Dictionary%602>或 派生,而不是實現介面。 這些類實現非泛型介面,從而在基本實現中包括對 XAML 集合的預期支援。

## <a name="read-only-collections-and-initialization-logic"></a>唯讀取與初始化邏輯

在 .NET 程式設計中,將保存集合值的任何屬性作為唯讀集合,是一種常見的設計模式。 此模式允許擁有集合屬性的實例更好地控制集合發生的情況。 具體而言,該模式通過設置屬性防止意外替換整個預先存在的集合。 在此模式中,調用方對集合的任何訪問都應該通過調用集合類型和/或相關集合介面(如<xref:System.Collections.IList>) 支援的方法或屬性進行。

使用此模式意味著公開唯讀集合屬性的任何類必須首先初始化該屬性以容納空集合。 通常,初始化是作為類構造行為的一部分執行的。 為了對 XAML 有用,無參數構造函數始終引用此類邏輯非常重要,因為 XAML 在處理屬性(集合屬性或其他)之前通常調用無參數構造函數。

## <a name="xaml-type-system-support-and-collections"></a>XAML 類型系統支援和集合

除了解析 XAML 和填充或序列化集合屬性的基本機制外,.NET XAML 服務中實現的 XAML 類型系統還包括與 XAML 中的集合相關的多個設計功能。

1. <xref:System.Xaml.XamlType.IsCollection%2A>如果 XAML 類型由提供 XAML 集合支援的類型支援,則返回 true。

2. <xref:System.Xaml.XamlType.IsDictionary%2A>並<xref:System.Xaml.XamlType.IsArray%2A>可以進一步識別 XAML 類型支援的集合模式。 對於基於 .NET XAML 服務和 XAML 類型<xref:System.Xaml.XamlWriter>系統但不基於現有 實現的自定義 XAML 處理器,可能需要瞭解使用哪種收集模式,以便知道要調用哪種方法來進行收集處理。

3. 以前的每個屬性值都可能受 XAML<xref:System.Xaml.XamlType.LookupCollectionKind%2A>類型的 重寫的影響。

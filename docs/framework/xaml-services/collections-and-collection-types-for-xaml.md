---
title: XAML 的集合和集合類型
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 63f6346837f77dbdbdcb4a90ec5af725be69ee02
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364333"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML 的集合和集合類型

本主題描述如何定義要支援集合的型別屬性, 以及支援將收集項具現化為父物件元素或 property 專案之專案子系的 XAML 語法。

## <a name="xaml-collection-concepts"></a>XAML 集合概念

就概念而言, XAML 中有多個子專案的任何關聯性, 都必須實作為集合。 該集合必須與 XAML 類型 (該關聯性中的父系) 的特定 XAML 屬性相關聯。 屬性必須是集合, 因為 XAML 處理器預期會將標記中的每個專案指派為支援集合屬性的新加入專案。

在 XAML 語言層級, 集合支援的確切需求並未完整定義。 集合可以是清單或字典 (但不是兩者) 的概念是在 XAML 語言層級定義, 但哪些支援類型代表清單或字典不是由 XAML 語言所定義。

在 .NET Framework XAML 服務中, XAML 集合支援的概念在 .NET Framework 支援類型方面更清楚地定義。 具體而言, 針對集合的 XAML 支援是根據一般 .NET Framework 程式設計中用於清單和字典的幾個 .NET Framework 概念和 Api。

1. <xref:System.Collections.IList>介面表示清單集合。

2. <xref:System.Collections.IDictionary>介面表示字典集合。

3. <xref:System.Array>表示陣列, 而陣列則支援<xref:System.Collections.IList>方法。

在上述每個集合概念中, .NET Framework xaml 服務 xaml 處理器預期會在集合`Add`屬性類型的特定實例上呼叫方法。 或者, 在序列化案例中, XAML 處理器會根據每個集合的「專案」概念, 針對清單、字典或陣列中找到的每個專案, 產生離散的 XAML 型別實例。 這些是: <xref:System.Collections.IList.Item%2A>;<xref:System.Array.System%23Collections%23IList%23Item%2A> ;的<xref:System.Array>明確。 <xref:System.Collections.IDictionary.Item%2A>

## <a name="generic-collections"></a>泛型集合

泛型集合適用于一般 .NET Framework 程式設計, 而且也可以用於 XAML 集合屬性。 不過, .NET Framework xaml 服務<xref:System.Collections.Generic.IList%601> xaml <xref:System.Collections.Generic.IDictionary%602>處理器與非泛型<xref:System.Collections.IList>或<xref:System.Collections.IDictionary>相等時, 不會識別泛型介面和。 泛型集合屬性類型的建議方法是衍生自類別<xref:System.Collections.Generic.List%601>或<xref:System.Collections.Generic.Dictionary%602>, 而不是執行介面。 這些類別會執行非泛型介面, 因此在基底實作為中包含 XAML 集合的預期支援。

## <a name="read-only-collections-and-initialization-logic"></a>唯讀集合和初始化邏輯

在 .NET Framework 程式設計中, 這是一種常見的設計模式, 可讓任何屬性將集合的值保存為唯讀集合。 此模式可讓擁有集合屬性的實例更有效地控制要對集合進行的動作。 具體而言, 模式會藉由設定屬性, 來防止意外取代整個預先存在的集合。 在此模式中, 由呼叫端對集合所做的任何存取, 應改為呼叫集合類型和/或相關集合介面 (例如) <xref:System.Collections.IList>所支援的方法或屬性。

使用此模式表示任何公開唯讀集合屬性的類別都必須先初始化該屬性, 以保存空的集合。 一般來說, 初始化會當做類別的結構行為之一部分來執行。 對於 XAML 很有用, 因為 XAML 通常會在處理屬性 (集合屬性或其他) 之前呼叫無參數的函式, 所以一定要由無參數的函式來參考這類邏輯。

## <a name="xaml-type-system-support-and-collections"></a>XAML 類型系統支援和集合

除了剖析 XAML 以及填入或序列化集合屬性的基本機制之外, 在 .NET Framework XAML 服務中實作為的 XAML 型別系統, 還包含數個與 XAML 集合相關的設計功能。

1. <xref:System.Xaml.XamlType.IsCollection%2A>如果 XAML 型別是以提供 XAML 集合支援的型別為後盾, 則傳回 true。

2. <xref:System.Xaml.XamlType.IsDictionary%2A>和<xref:System.Xaml.XamlType.IsArray%2A>可以進一步識別 XAML 類型支援的收集模式。 針對以 .NET Framework xaml 服務和 xaml 型別系統為基礎的自訂 xaml 處理器, 但不是<xref:System.Xaml.XamlWriter>以現有的實作為基礎, 知道要使用哪一個收集模式來知道要叫用的方法集合處理。

3. 上一個屬性值可能會受到 XAML 型別上之<xref:System.Xaml.XamlType.LookupCollectionKind%2A>覆寫的影響。

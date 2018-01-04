---
title: "XAML 的集合和集合類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
caps.latest.revision: "2"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67fec476c95d82b769494d53e50550cad0c719b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML 的集合和集合類型
本主題描述如何定義是用來支援一個集合，以及支援 XAML 語法產生做為父物件項目或屬性項目的項目子系的集合項目類型的屬性。  
  
## <a name="xaml-collection-concepts"></a>XAML 集合概念  
 就概念而言，任何關聯性在 XAML 中有多個子項目範圍內的 XAML 物件項目或集合必須實作 XAML 屬性項目位置。 該集合必須是父系的關聯性中的 XAML 類型的特定 XAML 內容相關聯。 屬性必須是集合，因為 XAML 處理器預期要指派標記，以新加入的項目備份集合屬性中的每個項目。  
  
 在 XAML 語言層級的集合支援的實際需求不會完整定義。 集合可以是其中一種清單或字典 （但非兩者） 的概念定義在 XAML 語言層級，但哪些備份類型代表任一清單或字典不由 XAML 語言定義。  
  
 在.NET Framework XAML 服務 XAML 集合支援的概念是以支援類型的.NET Framework 更清楚地定義的。 具體而言，XAML 支援，而集合根據數個.NET Framework 概念和 Api，用於清單和一般的.NET Framework 程式設計中的字典。  
  
1.  <xref:System.Collections.IList>介面會指示清單集合。  
  
2.  <xref:System.Collections.IDictionary>介面的指出 dicionary 的集合。  
  
3.  <xref:System.Array>支援陣列和陣列，代表<xref:System.Collections.IList>方法。  
  
 在每個這些集合的概念，.NET Framework XAML 服務 XAML 處理器預期呼叫`Add`特定執行個體的集合屬性的型別方法。 或者，在序列化案例中，XAML 處理器會產生每個項目清單、 字典或 「 項目 」 的每個集合的特定概念為基礎的陣列中所找到的離散 XAML 類型執行個體。 這些是： <xref:System.Collections.IList.Item%2A>;<xref:System.Collections.IDictionary.Item%2A>; 明確<xref:System.Array.System%23Collections%23IList%23Item%2A>如<xref:System.Array>。  
  
## <a name="generic-collections"></a>泛型集合  
 泛型集合可用於一般的.NET Framework 程式，並也用於 XAML 集合屬性。 不過，泛型介面<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>視為相當於非泛型的.NET Framework XAML 服務 XAML 處理器不會識別<xref:System.Collections.IList>或<xref:System.Collections.IDictionary>。 而不是實作的介面，是建議的方法，泛型集合的屬性類型是衍生自類別<xref:System.Collections.Generic.List%601>或<xref:System.Collections.Generic.Dictionary%602>。 這些類別實作非泛型介面，並且因此預期的支援 XAML 集合中的基底實作。  
  
## <a name="read-only-collections-and-initialization-logic"></a>唯讀的集合和初始化邏輯  
 在.NET Framework 程式設計中，它是集合的保留的值作為唯讀集合的任何屬性的一般設計模式。 此模式可讓擁有較佳的控制項集合會發生什麼情況的集合屬性的執行個體... 具體而言，模式會以防止意外取代整個預先存在的收集設定屬性。 在此模式中，任何集合的存取權的呼叫端應該改為透過呼叫方法或屬性，例如支援的集合型別和/或相關的集合介面<xref:System.Collections.IList>。  
  
 使用此模式表示任何公開唯讀的集合屬性的類別必須先初始化該屬性來保留空集合。 通常做為類別的建構行為的一部分執行初始化。 可用於 XAML，它是很重要的預設建構函式中，固定參考這類邏輯因為 XAML 通常會呼叫預設建構函式之前處理屬性 (集合屬性或其他)。  
  
## <a name="xaml-type-system-support-and-collections"></a>XAML 類型系統支援和集合  
 超出剖析 XAML 和填入或序列化集合屬性的基本機制，在.NET Framework XAML 服務中實作時，XAML 類型系統會包含數個設計功能與在 XAML 中的集合。  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A>如果提供 XAML 集合支援的型別所支援的 XAML 型別，傳回 true。  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A>和<xref:System.Xaml.XamlType.IsArray%2A>可以進一步指定 XAML 型別支援的收集模式。 自訂 XAML 的.NET Framework XAML 服務和 XAML 為基礎的處理器類型系統，但無法根據現有的<xref:System.Xaml.XamlWriter>實作中，了解使用的收集模式可能需要才能知道哪一種方法來叫用的收集處理程序。  
  
3.  每個先前屬性的值可能受到的覆寫<xref:System.Xaml.XamlType.LookupCollectionKind%2A>XAML 型別上。

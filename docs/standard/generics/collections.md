---
title: ".NET Framework 中的泛型集合"
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
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7e7d11446c14cffbef1e5cade5f082874187636
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="generic-collections-in-the-net-framework"></a>.NET Framework 中的泛型集合
本主題提供 .NET Framework 中泛型集合類別和其他泛型類型的概觀。  
  
## <a name="generic-collections-in-the-net-framework"></a>.NET Framework 中的泛型集合  
 .NET Framework 類別庫提供 <xref:System.Collections.Generic> 和 <xref:System.Collections.ObjectModel> 命名空間中的一些泛型集合類別。 如需這些類別的詳細資訊，請參閱[常用的集合類型](../../../docs/standard/collections/commonly-used-collection-types.md)。  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 許多泛型集合類型是非泛型類型的直接模擬。 <xref:System.Collections.Generic.Dictionary%602> 是 <xref:System.Collections.Hashtable> 的泛型版本，使用泛型結構 <xref:System.Collections.Generic.KeyValuePair%602> (而不是 <xref:System.Collections.DictionaryEntry>) 來進行列舉。  
  
 <xref:System.Collections.Generic.List%601> 是 <xref:System.Collections.ArrayList> 的泛型版本。 泛型 <xref:System.Collections.Generic.Queue%601> 和 <xref:System.Collections.Generic.Stack%601> 類別有對應的非泛型版本。  
  
 <xref:System.Collections.Generic.SortedList%602> 有泛型和非泛型版本。 這兩種版本是字典和清單的混合。 <xref:System.Collections.Generic.SortedDictionary%602> 泛型類別是純字典，沒有對應的非泛型版本。  
  
 <xref:System.Collections.Generic.LinkedList%601> 泛型類別是純連結清單， 沒有對應的非泛型版本。  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> 泛型類別提供基底類別，可用於衍生您自己的泛型集合類型。 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 類別提供一個簡單的方法，從任何實作 <xref:System.Collections.Generic.IList%601> 泛型介面的類型中產生唯讀集合。 <xref:System.Collections.ObjectModel.KeyedCollection%602> 泛型類別提供一個方法來儲存物件 (其中包含物件的索引鍵)。  
  
## <a name="other-generic-types"></a>其他泛型類型  
 <xref:System.Nullable%601> 泛型結構可讓您使用可指派 `null` 的實值類型。 這在使用資料庫查詢時會很有用，因為包含實值類型的欄位可能遺漏。 泛型類型參數可以是任何實值類型。  
  
> [!NOTE]
>  在 C# 中，不需要明確使用 <xref:System.Nullable%601>，因為這個語言具有可為 null 類型的語法。  
  
 <xref:System.ArraySegment%601> 泛型結構提供一個方法，將項目範圍限定在任何類型之以零為起始的一維陣列中。 泛型類型參數是陣列的項目類型。  
  
 如果您的事件遵循 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 所使用的事件處理模式，則 <xref:System.EventHandler%601> 泛型委派不需要宣告委派類型來處理事件。 例如，假設您已建立衍生自 <xref:System.EventArgs> 的 `MyEventArgs` 類別來保存事件的資料。 您可以接著依照下列方式來宣告事件：  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [泛型](../../../docs/standard/generics/index.md)  
 [管理陣列和清單的泛型委派](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [泛型介面](../../../docs/standard/generics/interfaces.md)

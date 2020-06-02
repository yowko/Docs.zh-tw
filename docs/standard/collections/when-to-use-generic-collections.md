---
title: 何時使用泛型集合
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: c59a125a8df95e3c4fe6e1839956d800bd6ee910
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290379"
---
# <a name="when-to-use-generic-collections"></a>何時使用泛型集合

使用泛型集合可提供型別安全的自動優點，而不需要衍生自基底集合型別和實作為型別特定成員。 當集合元素是實值型別時，泛型集合型別的效能通常會比對應的非泛型集合型別（而且比衍生自非泛型基底集合型別的類型更好），因為有了泛型，因此不需要將元素框在一起。

針對以 .NET Standard 1.0 或更新版本為目標的程式， <xref:System.Collections.Concurrent> 當多個執行緒可能同時新增或移除集合中的專案時，請使用命名空間中的泛型集合類別。 此外，如果需要不必要的，請考慮命名空間中的泛型集合類別 <xref:System.Collections.Immutable> 。

下列泛型類型對應至現有的集合類型：

- <xref:System.Collections.Generic.List%601> 是對應至 <xref:System.Collections.ArrayList>的泛型類別。

- <xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 是對應至 <xref:System.Collections.Hashtable>的泛型類別。

- <xref:System.Collections.ObjectModel.Collection%601> 是對應至 <xref:System.Collections.CollectionBase>的泛型類別。 <xref:System.Collections.ObjectModel.Collection%601>可以當做基類使用，但不同 <xref:System.Collections.CollectionBase> 于，它不是抽象的，這使得使用起來更容易。

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 是對應至 <xref:System.Collections.ReadOnlyCollectionBase>的泛型類別。 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>不是抽象的，而且具有可讓您輕鬆地將現有的公開 <xref:System.Collections.Generic.List%601> 為唯讀集合的函數。

- <xref:System.Collections.Generic.Queue%601>、 <xref:System.Collections.Concurrent.ConcurrentQueue%601> 、 <xref:System.Collections.Immutable.ImmutableQueue%601> 、 <xref:System.Collections.Immutable.ImmutableArray%601> 、 <xref:System.Collections.Generic.SortedList%602> 和 <xref:System.Collections.Immutable.ImmutableSortedSet%601> 泛型類別會對應至具有相同名稱的個別非泛型類別。

## <a name="additional-types"></a>其他類型

數個泛型集合類型沒有非泛型的對應項目。 其包括：

- <xref:System.Collections.Generic.LinkedList%601> 是提供 O(1) 插入和移除作業的一般用途連結清單。

- <xref:System.Collections.Generic.SortedDictionary%602> 是 O(log `n`) 插入和擷取作業的已排序字典，這讓它成為 <xref:System.Collections.Generic.SortedList%602>相當實用的替代方法。

- <xref:System.Collections.ObjectModel.KeyedCollection%602> 是清單與字典之間的混合體，它提供方法來儲存包含自己索引鍵的物件。

- <xref:System.Collections.Concurrent.BlockingCollection%601> 會實作具有週框和封鎖功能的集合類別。

- <xref:System.Collections.Concurrent.ConcurrentBag%601> 提供未排序項目的快速插入和移除。

### <a name="immutable-builders"></a>不可變的產生器

當您想要在應用程式中使用不可變性的功能時， <xref:System.Collections.Immutable> 命名空間會提供您可以使用的泛型集合類型。 所有不可變的集合類型都提供 `Builder` 可在您執行多個變化時優化效能的類別。 `Builder`類別會以可變狀態批次作業。 當所有變化都完成時，請呼叫 `ToImmutable` 方法以「凍結」所有節點，並建立不可變的泛型集合，例如 <xref:System.Collections.Immutable.ImmutableList%601> 。

您 `Builder` 可以藉由呼叫非泛型方法來建立物件 `CreateBuilder()` 。 `Builder`您可以從實例呼叫 `ToImmutable()` 。 同樣地，從 `Immutable*` 集合中，您可以呼叫， `ToBuilder()` 以從泛型不可變集合建立產生器實例。 以下是各種 `Builder` 類型。

- <xref:System.Collections.Immutable.ImmutableArray%601.Builder>
- <xref:System.Collections.Immutable.ImmutableDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableHashSet%601.Builder>
- <xref:System.Collections.Immutable.ImmutableList%601.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder>

## <a name="linq-to-objects"></a>LINQ to Objects

只要物件類型實作 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面，LINQ to Objects 功能就可讓您使用 LINQ 查詢以存取記憶體中的物件。 LINQ 查詢提供存取資料的常見模式;通常比標準迴圈更精簡且更容易閱讀， `foreach` 並提供篩選、排序和群組功能。 LINQ 查詢也可以提升效能。 如需詳細資訊，請參閱 [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md)、[LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) 和 [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md)。

## <a name="additional-functionality"></a>其他功能
某些泛型類型具有非泛型集合類型中找不到的功能。 例如， <xref:System.Collections.Generic.List%601> 類別 (對應至非泛型 <xref:System.Collections.ArrayList> 類別) 有許多接受泛型委派的方法，例如 <xref:System.Predicate%601> 委派 (允許您指定方法來搜尋清單)、 <xref:System.Action%601> 委派 (代表對清單每個項目採取動作的方法)，以及 <xref:System.Converter%602> 委派 (可定義類型之間的轉換)。

<xref:System.Collections.Generic.List%601> 類別可讓您指定自己的 <xref:System.Collections.Generic.IComparer%601> 泛型介面實作，以排序及搜尋清單。 <xref:System.Collections.Generic.SortedDictionary%602> 和 <xref:System.Collections.Generic.SortedList%602> 類別也具有這項功能。 此外，這些類別可讓您在建立集合時，指定比較子。 <xref:System.Collections.Generic.Dictionary%602> 和 <xref:System.Collections.ObjectModel.KeyedCollection%602> 類別會以類似的方式，讓您能指定自己的相等比較子。

## <a name="see-also"></a>另請參閱

- [集合和資料結構](index.md)
- [常用的集合類型](commonly-used-collection-types.md)
- [泛型](../generics/index.md)

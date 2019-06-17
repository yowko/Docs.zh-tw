---
title: 泛型介面
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- generic interfaces [.NET Framework]
- equality comparisons [.NET Framework]
- generics [.NET Framework], interfaces
- ordering comparisons [.NET Framework]
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9570578e8ae4397f060805b891f86d7d4f273cd4
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487039"
---
# <a name="generic-interfaces"></a>泛型介面
本主題概述提供泛型類型系列中常見功能的泛型介面。  
  
## <a name="generic-interfaces"></a>泛型介面  
 泛型介面提供非泛型介面的類型安全對應項目，以進行排序和相等比較，以及泛型集合類型的功能。  
  
> [!NOTE]
>  從 .NET Framework 4 開始，數個泛型介面的型別參數會標示共變數或反變數，提供更大彈性來指派和使用實作這些介面的型別。 請參閱 [共變數和反變數](../../../docs/standard/generics/covariance-and-contravariance.md)。  
  
### <a name="equality-and-ordering-comparisons"></a>相等和排序比較  
 在 <xref:System> 命名空間中，<xref:System.IComparable%601?displayProperty=nameWithType> 和 <xref:System.IEquatable%601?displayProperty=nameWithType> 泛型介面 (就像其非泛型對應項目) 分別會定義排序比較相等比較的方法。 類型會實作這些介面，以提供執行這類比較的能力。  
  
 在 <xref:System.Collections.Generic> 命名空間中，<xref:System.Collections.Generic.IComparer%601> 和 <xref:System.Collections.Generic.IEqualityComparer%601> 泛型介面有提供一種方式，可針對沒有實作 <xref:System.IComparable%601?displayProperty=nameWithType> 或 <xref:System.IEquatable%601?displayProperty=nameWithType> 泛型介面的類型，定義排序或相等比較，並針對有實作該泛型介面的類型，提供重新定義這些關聯性的方式。 許多泛用集合類別的方法和建構函式都會使用這些介面。 例如，您可以傳遞泛型 <xref:System.Collections.Generic.IComparer%601> 物件至 <xref:System.Collections.Generic.SortedDictionary%602> 類別的建構函式，以針對沒有實作泛型 <xref:System.IComparable%601?displayProperty=nameWithType> 的類型，指定排序順序。 有 <xref:System.Array.Sort%2A?displayProperty=nameWithType> 泛型靜態方法和 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 執行個體方法的多載，可以使用泛型 <xref:System.Collections.Generic.IComparer%601> 實作來排序陣列和清單。  
  
 <xref:System.Collections.Generic.Comparer%601> 和 <xref:System.Collections.Generic.EqualityComparer%601> 泛型類別為 <xref:System.Collections.Generic.IComparer%601> 和 <xref:System.Collections.Generic.IEqualityComparer%601> 泛型介面的實作提供基底類別，同時也透過其各自 <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=nameWithType> 屬性，提供預設的排序和相等比較。  
  
### <a name="collection-functionality"></a>集合功能  
 <xref:System.Collections.Generic.ICollection%601> 泛型介面是泛型集合類型的基本介面。 它提供用來新增、移除、複製和列舉項目的基本功能。 <xref:System.Collections.Generic.ICollection%601> 同時繼承自泛型 <xref:System.Collections.Generic.IEnumerable%601> 和非泛型 <xref:System.Collections.IEnumerable>。  
  
 <xref:System.Collections.Generic.IList%601> 泛型介面會使用編製索引的擷取方法來擴充 <xref:System.Collections.Generic.ICollection%601> 泛型介面。  
  
 <xref:System.Collections.Generic.IDictionary%602> 泛型介面會使用索引鍵的擷取方法來擴充 <xref:System.Collections.Generic.ICollection%601> 泛型介面。 .NET Framework 基底類別庫中的泛型字典類型也會實作非泛型 <xref:System.Collections.IDictionary> 介面。  
  
 <xref:System.Collections.Generic.IEnumerable%601> 泛型介面提供泛型列舉程式結構。 泛型列舉程式所實作的 <xref:System.Collections.Generic.IEnumerator%601> 泛型介面會繼承非泛型 <xref:System.Collections.IEnumerator> 介面；<xref:System.Collections.IEnumerator.MoveNext%2A> 和 <xref:System.Collections.IEnumerator.Reset%2A> 成員 (不相依於類型參數 `T`) 只會出現在泛型介面上。 這表示非泛型介面的任何消費者也都可以使用泛型介面。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [泛型](../../../docs/standard/generics/index.md)
- [.NET Framework 中的泛型集合](../../../docs/standard/generics/collections.md)
- [管理陣列和清單的泛型委派](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [共變數和反變數](../../../docs/standard/generics/covariance-and-contravariance.md)

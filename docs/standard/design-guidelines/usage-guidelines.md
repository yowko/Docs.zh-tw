---
title: 使用指導方針
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: d6ea7c7b9ada95e3d0c425aaea18be6cdbb4ce35
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828500"
---
# <a name="usage-guidelines"></a>使用指導方針

本節包含在可公開存取的 Api 中使用一般類型的指導方針。 它會處理內建架構類型的直接使用 (例如，序列化屬性) 和多載一般運算子。
  
<xref:System.IDisposable?displayProperty=nameWithType>此節並未涵蓋介面，但會在[Dispose 模式](../garbage-collection/implementing-dispose.md)區段中討論。

> [!NOTE]
> 如需其他常見、內建 .NET Framework 類型的指導方針及其他資訊，請參閱下列的參考主題： <xref:System.DateTime?displayProperty=nameWithType> 、 <xref:System.DateTimeOffset?displayProperty=nameWithType> 、 <xref:System.ICloneable?displayProperty=nameWithType> 、 <xref:System.IComparable%601?displayProperty=nameWithType> 、 <xref:System.IEquatable%601?displayProperty=nameWithType> 、 <xref:System.Nullable%601?displayProperty=nameWithType> 、 <xref:System.Object?displayProperty=nameWithType> 、 <xref:System.Uri?displayProperty=nameWithType> 。

## <a name="in-this-section"></a>本節內容

[陣列](arrays.md)  
[屬性](attributes.md)  
[集合](guidelines-for-collections.md)  
[序列化](serialization.md)  
[System.Xml 使用方式](system-xml-usage.md)  
[等號比較運算子](equality-operators.md)  

*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。
  
## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)

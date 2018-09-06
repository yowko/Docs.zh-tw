---
title: 使用指導方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e44a6b58fd334b6a23e113922b980f69de627b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869862"
---
# <a name="usage-guidelines"></a>使用指導方針

本章節包含使用可公開存取的 Api 中的常見類型的指導方針。 它處理的內建的 Framework 類型 （例如，序列化的屬性） 和常見的運算子多載化方式使用。
  
<xref:System.IDisposable?displayProperty=nameWithType>介面未涵蓋在本節中，但會討論[Dispose 模式](../../../docs/standard/design-guidelines/dispose-pattern.md)一節。

> [!NOTE]
> 如指導方針和其他常見的相關其他相關資訊，內建的.NET Framework 型別，請參閱下列參考主題： <xref:System.DateTime?displayProperty=nameWithType>， <xref:System.DateTimeOffset?displayProperty=nameWithType>， <xref:System.ICloneable?displayProperty=nameWithType>， <xref:System.IComparable%601?displayProperty=nameWithType>， <xref:System.IEquatable%601?displayProperty=nameWithType>， <xref:System.Nullable%601?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.

## <a name="in-this-section"></a>本節內容

[陣列](arrays.md)  
[屬性](attributes.md)  
[集合](guidelines-for-collections.md)  
[序列化](serialization.md)  
[System.Xml 使用方式](system-xml-usage.md)  
[等號比較運算子](equality-operators.md)  

*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

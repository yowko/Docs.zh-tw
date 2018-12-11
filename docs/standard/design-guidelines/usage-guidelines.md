---
title: 使用指導方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 761570b899a2a36391eb81dc7f42e13fff1f14ef
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155401"
---
# <a name="usage-guidelines"></a>使用指導方針

本章節包含使用可公開存取的 Api 中的常見類型的指導方針。 它處理的內建的 Framework 類型 （例如，序列化的屬性） 和常見的運算子多載化方式使用。
  
<xref:System.IDisposable?displayProperty=nameWithType>介面未涵蓋在本節中，但會討論[Dispose 模式](../../../docs/standard/design-guidelines/dispose-pattern.md)一節。

> [!NOTE]
> 如需指導方針和其他常見的其他資訊，內建的.NET Framework 型別，請參閱下列參考主題： <xref:System.DateTime?displayProperty=nameWithType>， <xref:System.DateTimeOffset?displayProperty=nameWithType>， <xref:System.ICloneable?displayProperty=nameWithType>， <xref:System.IComparable%601?displayProperty=nameWithType>， <xref:System.IEquatable%601?displayProperty=nameWithType>， <xref:System.Nullable%601?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.

## <a name="in-this-section"></a>本節內容

[陣列](arrays.md)  
[屬性](attributes.md)  
[集合](guidelines-for-collections.md)  
[序列化](serialization.md)  
[System.Xml 使用方式](system-xml-usage.md)  
[等號比較運算子](equality-operators.md)  

*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*

*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

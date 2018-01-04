---
title: "用法方針"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3f0a38c69dc286587e702b80ef4093bb98d78b5a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="usage-guidelines"></a>用法方針
本章節包含使用一般類型，可公開存取的 Api 中的指導方針。 它說明如何直接使用內建架構類型 （例如序列化屬性） 和一般運算子多載。  
  
 <xref:System.IDisposable?displayProperty=nameWithType>介面未涵蓋在本節中，但在討論[Dispose 模式](../../../docs/standard/design-guidelines/dispose-pattern.md)> 一節。  
  
> [!NOTE]
>  指導方針和其他常見的相關其他相關資訊，如內建的.NET Framework 型別，請參閱下列參考主題： <xref:System.DateTime?displayProperty=nameWithType>， <xref:System.DateTimeOffset?displayProperty=nameWithType>， <xref:System.ICloneable?displayProperty=nameWithType>， <xref:System.IComparable%601?displayProperty=nameWithType>， <xref:System.IEquatable%601?displayProperty=nameWithType>， <xref:System.Nullable%601?displayProperty=nameWithType>， <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.  
  
## <a name="in-this-section"></a>本節內容  
 [陣列](../../../docs/standard/design-guidelines/arrays.md)  
 [屬性](../../../docs/standard/design-guidelines/attributes.md)  
 [集合](/cpp/mfc/collections)  
 [序列化](../../../docs/standard/design-guidelines/serialization.md)  
 [System.Xml 使用方式](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [等號比較運算子](../../../docs/standard/design-guidelines/equality-operators.md)  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

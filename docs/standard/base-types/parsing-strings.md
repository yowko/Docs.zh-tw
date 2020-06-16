---
title: 在 .NET 中剖析字串
description: 瞭解 .NET 中的字串剖析。 剖析會將代表 .NET 基底類型的字串轉換成該基底類型。 剖析是格式化的反向作業。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769284"
---
# <a name="parsing-strings-in-net"></a>在 .NET 中剖析字串
剖析作業會將代表 .NET 基底類型的字串轉換成該基底類型。 例如，剖析作業用來將字串轉換為浮點數或日期和時間值。 最常用來執行剖析作業的方法是 `Parse` 方法。 因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。 就像格式化會使用實作 <xref:System.IFormatProvider> 介面的物件來提供區分文化特性的格式化資訊，剖析也會使用實作 <xref:System.IFormatProvider> 介面的物件來判斷如何解譯字串表示。 如需詳細資訊，請參閱[格式類型](formatting-types.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [剖析數值字串](parsing-numeric.md)  
 描述如何將字串轉換成 .NET 數值類型。  
  
 [剖析日期和時間字串](parsing-datetime.md)  
 描述如何將字串轉換成 .NET **DateTime** 類型。  
  
 [剖析其他字串](parsing-other.md)  
 描述如何將字串轉換成 **Char**、**Boolean** 和 **Enum** 類型。  
  
## <a name="related-sections"></a>相關章節  
 [格式化類型](formatting-types.md)  
 描述基本的格式化概念，例如格式規範和格式提供者。  
  
 [.NET 中的類型轉換](type-conversion.md)  
 描述如何轉換類型。

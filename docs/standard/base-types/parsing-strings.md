---
title: 將字串轉換成類型
description: 瞭解 .NET 中的字串剖析。 剖析會將代表 .NET 基底類型的字串轉換成該基底類型。 剖析是格式化的反向操作。
ms.date: 03/30/2017
ms.topic: conceptual
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: ff357f8b8225c84e2f6c0e022b269f0ab774dfed
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692847"
---
# <a name="parse-strings-in-net"></a>在 .NET 中剖析字串

*剖析* 作業會將代表 .net 基底類型的字串轉換成該基底類型。 例如，剖析作業會用來將字串轉換成浮點數或日期和時間值。 最常用來執行剖析作業的方法是 `Parse` 方法。 因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。 就像格式化會使用實作 <xref:System.IFormatProvider> 介面的物件來提供區分文化特性的格式化資訊，剖析也會使用實作 <xref:System.IFormatProvider> 介面的物件來判斷如何解譯字串表示。 如需詳細資訊，請參閱 [格式類型](formatting-types.md)。

## <a name="in-this-section"></a>本節內容

 [剖析數值字串](parsing-numeric.md)\
 描述如何將字串轉換成 .NET 數值類型。

 [剖析日期和時間字串](parsing-datetime.md)\
 描述如何將字串轉換成 .NET **DateTime** 類型。

 [剖析其他字串](parsing-other.md)\
 描述如何將字串轉換成 **Char**、**Boolean** 和 **Enum** 類型。

## <a name="related-sections"></a>相關章節

 [格式化類型](formatting-types.md)\
 描述基本的格式化概念，例如格式規範和格式提供者。

 [.NET 中的類型轉換](type-conversion.md)\
 描述如何轉換類型。

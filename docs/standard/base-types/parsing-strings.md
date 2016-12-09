---
title: "在 .NET 中剖析字串"
description: "在 .NET 中剖析字串"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 066c721e66192658ae841721c90c194686a0730d

---

# <a name="parsing-strings-in-net"></a>在 .NET 中剖析字串

剖析作業會將代表 .NET 基底類型的字串轉換成該基底類型。 例如，剖析作業用來將字串轉換為浮點數或日期和時間值。 最常用來執行剖析作業的方法是 `Parse` 方法。 因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。 當格式化使用實作 [IFormatProvider](xref:System.IFormatProvider) 介面的物件提供區分文化特性的格式資訊時，剖析也會使用實作 [IFormatProvider](xref:System.IFormatProvider) 介面的物件判斷如何解譯字串表示。 如需詳細資訊，請參閱[在 .NET 中格式化類型](formatting-types.md)。

## <a name="in-this-section"></a>本章節內容

[在 .NET 中剖析數值字串](parsing-numeric.md)：說明如何將字串轉換成 .NET 數值類型。

[在 .NET 中剖析日期和時間字串](parsing-datetime.md)：說明如何將字串轉換成 .NET `DateTime` 類型。

[在 .NET 中剖析其他字串](parsing-other.md)：說明如何將字串轉換成 [Char](xref:System.Char)、[Boolean](xref:System.Boolean) 和 [Enum](xref:System.Enum) 類型。

[在 .NET 中格式化類型](formatting-types.md)：描述基本的格式化概念，例如格式規範和格式提供者。

[.NET 口的類型轉換](type-conversion.md)：說明如何轉換類型。

[在 .NET 中使用基底類型](index.md)：說明您可以對 .NET 基底類型執行的一般作業。




<!--HONumber=Nov16_HO3-->



---
title: "在.NET 中剖析字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 811db42e04e73d7acbc03e303297b19fdf643384
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-strings-in-net"></a>在.NET 中剖析字串
剖析作業會將代表 .NET 基底類型的字串轉換成該基底類型。 例如，剖析作業用來將字串轉換為浮點數或日期和時間值。 最常用來執行剖析作業的方法是 `Parse` 方法。 因為剖析是格式設定的反向作業 (這牽涉到將基底類型別轉換成其字串表示)，所以會套用許多相同的規則和慣例。 只在格式化時使用該物件會實作<xref:System.IFormatProvider>介面，以提供區分文化特性格式資訊，剖析也會使用該物件會實作<xref:System.IFormatProvider>介面，以決定如何解譯的字串表示法. 如需詳細資訊，請參閱[格式化型別](../../../docs/standard/base-types/formatting-types.md)。  
  
## <a name="in-this-section"></a>本章節內容  
 [剖析數值字串](../../../docs/standard/base-types/parsing-numeric.md)  
 描述如何將字串轉換成.NET 數字型別。  
  
 [剖析日期和時間字串](../../../docs/standard/base-types/parsing-datetime.md)  
 描述如何將字串轉換成.NET **DateTime**型別。  
  
 [剖析其他字串](../../../docs/standard/base-types/parsing-other.md)  
 描述如何將轉換成字串**Char**，**布林**，和**列舉**型別。  
  
## <a name="related-sections"></a>相關章節  
 [格式化類型](../../../docs/standard/base-types/formatting-types.md)  
 描述基本格式的概念，像是格式規範和格式提供者。  
  
 [.NET 中的類型轉換](../../../docs/standard/base-types/type-conversion.md)  
 描述如何將類型轉換。  
  
 [基底類型](../../../docs/standard/base-types/index.md)  
 描述您可以在.NET 基底類型執行的一般作業。

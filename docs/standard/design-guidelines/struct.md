---
title: "結構設計"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1566d2b67e1dda5b0b221a2c10affb6bdaea888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="struct-design"></a>結構設計
一般用途的實值類型通常稱為結構，其 C# 關鍵字。 本節提供一般結構設計指導方針。  
  
 **X 不**結構提供的預設建構函式。  
  
 遵循這個指導方針可讓結構來建立，而不需要在陣列的每個項目上執行建構函式的陣列。 請注意，C# 不允許有預設建構函式的結構。  
  
 **X 不**定義可變動的值型別。  
  
 可變動的值型別有幾個問題。 例如，當屬性 getter 傳回實值類型時，呼叫端接收複本。 因為隱含地建立複本時，開發人員可能不會察覺複製，而非原始的值會變更。 此外，某些語言 （特別是，動態語言） 具有區域變數，即使是取值時，會導致複本可供使用，因為可變動的實值類型的問題。  
  
 **✓ 不要**確保所有執行個體資料的狀態設為零，false 或 null （視情況） 無效。  
  
 建立結構的陣列時，這可防止意外建立無效的執行個體。  
  
 **✓ 不要**實作<xref:System.IEquatable%601>實值型別。  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>實值類型上的方法會導致 boxing，和其預設實作不是非常有效率，因為它會使用反映。 <xref:System.IEquatable%601.Equals%2A>可能會較佳的效能，而且可以實作，使它不會造成 boxing。  
  
 **X 不**明確地延長<xref:System.ValueType>。 事實上，大部分語言防止這。  
  
 一般情況下，結構就非常有用，但僅用於小型、 單一、 不可變會不會進行 boxed 處理經常的值。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [型別設計指導方針](../../../docs/standard/design-guidelines/type.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [類別和結構之間選擇](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)

---
title: 結構設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3879dc3f0270a56132b44882a74c50d05914ff89
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324616"
---
# <a name="struct-design"></a>結構設計
一般用途的實值型別最常稱為結構時，它的 C# 關鍵字。 本節提供一般的結構設計指導方針。  
  
 **X DO NOT** 結構提供的預設建構函式。  
  
 遵循此指導方針，可讓建立而不需陣列的每個項目上執行建構函式的結構陣列。 請注意，C# 不允許有預設建構函式的結構。  
  
 **X DO NOT** 定義可變動的值型別。  
  
 可變動的實值型別有幾個問題。 例如，當屬性 getter 傳回實值型別時，呼叫端會收到複本。 因為隱含地建立複本時，可能不知道複本，而不是原始的值會變更開發人員。 此外，某些語言 （特別是，動態語言） 有取值時，甚至是本機變數，會造成複本設為使用可變動的實值型別，因為的問題。  
  
 **✓ DO** 確保所有執行個體資料的狀態設為零，false 或 null （視情況） 無效。  
  
 建立結構的陣列時，這會防止意外建立無效的執行個體。  
  
 **✓ DO** 實作 <xref:System.IEquatable%601> 實值型別。  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>實值型別上的方法會導致 boxing，和其預設實作不是非常有效率，因為它會使用反映。 <xref:System.IEquatable%601.Equals%2A> 可以有更好的效能，並使它不會造成 boxing 可以實作。  
  
 **X DO NOT** 明確地延長 <xref:System.ValueType>。 事實上，大部分語言避免這個問題。  
  
 一般情況下，結構可以很有幫助，但僅用於小型、 單一、 不可變的值，將不會進行 boxed 處理常見問題。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [在類別和結構之間選擇](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)

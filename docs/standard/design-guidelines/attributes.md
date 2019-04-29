---
title: 屬性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 6d4cc6615b7f7346e9c8fc2a7264025f318c8a3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785563"
---
# <a name="attributes"></a>屬性
<xref:System.Attribute?displayProperty=nameWithType> 用來定義自訂屬性的基底類別。  
  
 屬性是可以加入至程式設計項目，例如組件、 類型、 成員和參數的註解。 它們會儲存在組件的中繼資料，而且可以在執行階段使用反映 Api 存取。 比方說，架構會定義<xref:System.ObsoleteAttribute>，它可以套用至類型或成員，表示型別或成員已被取代。  
  
 屬性可以有一或多個含有與屬性相關的其他資料的屬性。 比方說，`ObsoleteAttribute`無法執行的版本中的其他資訊類型或成員已過時和新的 Api 取代過時的 API 的描述。  
  
 套用屬性時，就必須指定屬性的某些屬性。 這些稱為必要的屬性或必要的引數，因為它們表示做為位置建構函式參數。 例如，<xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A>屬性<xref:System.Diagnostics.ConditionalAttribute>是必要的屬性。  
  
 選擇性的屬性 （或選擇性引數），會呼叫不一定有套用屬性時指定的屬性。 所表示的可設定的屬性。 編譯器會提供特殊的語法，來設定這些屬性時將套用的屬性。 比方說，<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>屬性表示選擇性的引數。  
  
 **✓ DO** 自訂屬性的後置詞的類別命名為 「 屬性 」。  
  
 **✓ DO** 套用 <xref:System.AttributeUsageAttribute> 自訂屬性。  
  
 **✓ DO** 提供選擇性引數的可設定的屬性。  
  
 **✓ DO** 屬性僅提供必要的引數。  
  
 **✓ DO** 提供初始化屬性對應到必要的引數的建構函式參數。 每個參數應為對應的屬性有相同的名稱 （但仍會有不同的大小寫）。  
  
 **X AVOID** 提供初始化屬性對應至選擇性引數的建構函式參數。  
  
 換句話說，不需要可以設定具有一個建構函式和 setter 的屬性。 這項指導方針可非常明確，哪些引數是選擇性的這是必要的並避免有兩種方式執行相同的動作。  
  
 **X AVOID** 自訂屬性建構函式多載。  
  
 只能有一個建構函式明確地溝通使用者哪些引數，且需何者為選擇性。  
  
 **✓ DO** 儘可能封裝自訂屬性的類別。 這可讓屬性查閱更快。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)

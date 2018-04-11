---
title: Attributes1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 89e892a379c7540cf67488471ae5281a4c4b86f4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="attributes"></a>屬性
<xref:System.Attribute?displayProperty=nameWithType>是基底類別，用來定義自訂屬性。  
  
 屬性是可以加入至程式設計項目，例如組件、 類型、 成員和參數的註解。 它們會儲存在組件的中繼資料，而且可以在執行階段使用反映 Api 存取。 例如，架構會定義<xref:System.ObsoleteAttribute>，可以套用至類型或成員，表示類型或成員已被取代。  
  
 屬性可以有一或多個執行其他資料與屬性相關的屬性。 例如，`ObsoleteAttribute`無法執行的版本中的其他資訊的類型或成員已被取代，而描述為新的 Api 取代過時的 API。  
  
 套用屬性時，就必須指定屬性的某些屬性。 這些稱為必要的屬性或必要的引數，因為它們以位置的建構函式參數。 例如，<xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A>屬性<xref:System.Diagnostics.ConditionalAttribute>是必要的屬性。  
  
 選擇性的屬性 （或選擇性引數），會呼叫不一定需要指定已套用該屬性的屬性。 所表示的可設定的屬性。 編譯器提供特殊的語法，來套用屬性時設定這些屬性。 例如，<xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType>屬性表示選擇性的引數。  
  
 **✓ 不要**自訂屬性的後置詞的類別命名為 「 屬性 」。  
  
 **✓ 不要**套用<xref:System.AttributeUsageAttribute>自訂屬性。  
  
 **✓ 不要**提供選擇性引數的可設定的屬性。  
  
 **✓ 不要**屬性僅提供必要的引數。  
  
 **✓ 不要**提供初始化屬性對應到必要的引數的建構函式參數。 每個參數應該具有相同的名稱 （但仍會有不同的大小寫） 做為對應的屬性。  
  
 **請避免 x**提供初始化屬性對應至選擇性引數的建構函式參數。  
  
 也就是說，不需要可以設定具有一個建構函式和 setter 的屬性。 這個指導方針可讓非常明確的引數是選擇性的這是必要的並避免有兩個介面的操作方式相同。  
  
 **請避免 x**自訂屬性建構函式多載。  
  
 包含只有一個建構函式可清楚地使用者哪些引數是必要、 哪些是選擇性。  
  
 **✓ 不要**儘可能封裝自訂屬性的類別。 這可讓屬性查閱更快。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)

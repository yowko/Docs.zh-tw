---
title: 實作抽象的基底類別
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: KrzysztofCwalina
ms.openlocfilehash: 6811423258481fcbae24743c9b17f3f20c379c58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565809"
---
# <a name="base-classes-for-implementing-abstractions"></a>實作抽象的基底類別
嚴格來說，類別就變得基底類別衍生自此類別的另一個類別。 不過，為了本章節中，基底類別是設計主要是為了提供常見的抽象概念，或重複使用一些其他類別的預設實作透過繼承的類別。 基底類別通常位於繼承階層架構，在階層的根的抽象概念與數個在底部的自訂實作之間的中間。  
  
 它們可當做實作協助程式實作抽象的。 例如，其中一個項目的已排序集合的架構的抽象概念是<xref:System.Collections.Generic.IList%601>介面。 實作<xref:System.Collections.Generic.IList%601>並非易事，因此架構可提供數個基底類別，例如<xref:System.Collections.ObjectModel.Collection%601>和<xref:System.Collections.ObjectModel.KeyedCollection%602>，其中實作自訂的集合做為協助程式。  
  
 基底類別通常不適合作為抽象概念，本身，因為它們通常包含太多的實作。 例如，`Collection<T>`基底類別包含許多相關的事實，它會實作非泛型實作`IList`介面 （若要整合更理想與非泛型集合），並實際上它是一組項目儲存在它的一個欄位中的記憶體。  
  
 如先前所述，基底類別必須實作的抽象的使用者可以提供寶貴的說明，但同時也很重要的責任。 它們加入介面區和增加的繼承階層架構的深度，以及因此在概念上會讓複雜的架構。 因此，它們提供重大價值架構的使用者時，才應該使用基底類別。 它們應盡可能它們才能 framework 中，應該強烈考慮的內部實作，而不是繼承自基底類別的案例委派的實作，提供值。  
  
 **✓ CONSIDER** 讓基底類別的抽象，即使它們不包含任何抽象成員。 如此可清楚的使用者，該類別只可繼承自。  
  
 **✓ CONSIDER** 置於不同的命名空間從主線情節類型的基底類別。 根據定義，基底類別適用的進階擴充性案例，因此不需要大部分的使用者。  
  
 **X AVOID** 命名基底類別具有 「 基底"後置詞，如果類別是用於在公用 Api。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

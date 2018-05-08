---
title: 實作抽象的基底類別
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c247ed7273687dbd61a6f19923b71e07e9ed960
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="base-classes-for-implementing-abstractions"></a>實作抽象的基底類別
嚴格來說，當另一個類別會從其衍生類別成為基底類別。 不過，為了本節中，基底類別是主要設計成提供的通用抽象概念，或重複使用一些其他類別的預設實作透過繼承的類別。 繼承階層架構的抽象概念，在階層的根和數個在底部的自訂實作之間的中間通常坐基底類別。  
  
 它們會充當實作 helper 實作抽象的。 例如，其中一個項目的已排序集合的架構的抽象概念是<xref:System.Collections.Generic.IList%601>介面。 實作<xref:System.Collections.Generic.IList%601>並非易事，並因此架構提供數個基底類別，例如<xref:System.Collections.ObjectModel.Collection%601>和<xref:System.Collections.ObjectModel.KeyedCollection%602>，其做為 helper 實作自訂的集合。  
  
 基底類別通常不適合作為抽象本身，因為它們通常包含太多的實作。 例如，`Collection<T>`基底類別包含許多相關的事實，它會實作非泛型實作`IList`介面 （若要進一步整合非泛型集合），並在於它是集合的項目儲存在其中一個欄位中的記憶體。  
  
 如先前所討論，基底類別必須實作的抽象概念的使用者可以提供有用的說明，但它們可以同時是重大的負擔。 它們加入介面區和增加的繼承階層架構的深度，以及因此在概念上使得架構。 因此，它們提供重大價值架構的使用者，才應該使用基底類別。 它們應該避免如果它們的 framework，應強視為案例委派的內部實作，而非繼承自基底類別實作器，才能提供的值。  
  
 **✓ 考慮**讓基底類別的抽象，即使它們不包含任何抽象成員。 如此可清楚的使用者，此類別的設計只是要繼承自。  
  
 **✓ 考慮**置於不同的命名空間從主線情節類型的基底類別。 根據定義，基底類別是針對進階的擴充性情節，因此無法興趣大部分的使用者。  
  
 **請避免 x**命名基底類別具有 「 基底"後置詞，如果類別是用於在公用 Api。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

---
title: 密封
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7202e10e41b9f114f42a4502ee2e6694bf3821
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573732"
---
# <a name="sealing"></a>密封
物件導向架構的功能之一是開發人員可以擴充並自訂架構設計人員所預期的方式。 這是設計的電源和可延伸的危險。 當您設計您的架構時，它是，因此，它需要時，小心設計擴充性，並限制危險時的擴充性非常重要。  
  
 強大的機制，可防止擴充性密封。 您可以密封類別或個別成員。 密封類別，可防止使用者從類別繼承。 密封成員可防止使用者覆寫特定成員。  
  
 **X DO NOT**密封類別有充分的理由，若要這樣做。  
  
 密封類別，因為您無法將擴充性案例不是很好的理由。 架構的使用者想要基於各種 nonobvious 原因的詳細資訊，例如新增方便成員繼承自類別。 請參閱[非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)nonobvious 原因的範例使用者想要繼承自型別。  
  
 密封類別的原因包括：  
  
-   此類別是靜態的類別。 請參閱[靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)。  
  
-   類別會繼承的 protected 成員中儲存機密的機密資料。  
  
-   類別繼承許多虛擬成員，而且個別密封它們的成本會超過優點可能會留下未密封的類別。  
  
-   此類別是需要非常快速的執行階段查閱的屬性。 密封的屬性具有稍微較高的效能層級比未密封。 請參閱[屬性](../../../docs/standard/design-guidelines/attributes.md)。  
  
 **X DO NOT**在密封類型上宣告受保護或虛擬的成員。  
  
 根據定義，密封的類型無法繼承自中。 這表示無法呼叫密封類型上的受保護的成員，而且不能覆寫虛擬方法，密封類型上。  
  
 **✓ CONSIDER**密封您覆寫的成員。  
  
 可能是因為簡介虛擬成員的問題 (討論[虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)) 套用於覆寫，雖然稍微較低刻度。 密封覆寫保護不受影響您從該階層架構中的點開始這些問題。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)

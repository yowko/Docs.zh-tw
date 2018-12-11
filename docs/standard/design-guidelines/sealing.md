---
title: 密封
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: KrzysztofCwalina
ms.openlocfilehash: fd1abdb4ff6f4850eea96bcfc3afbfe00a4ae56a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127689"
---
# <a name="sealing"></a>密封
物件導向的架構功能之一是開發人員可以擴充並自訂它們以非預期的架構設計人員的方式。 這是設計的電源和可延伸的危險。 當您設計您的架構時，它，因此它是時需要它，則應該仔細設計擴充性，以及限制擴充性，會有問題時非常重要。  
  
 功能強大的機制，以防止擴充性密封。 您可以密封類別或個別成員。 密封類別，可防止使用者從類別繼承。 密封的成員，可防止使用者覆寫特定成員。  
  
 **X DO NOT** 密封類別有充分的理由，若要這樣做。  
  
 密封類別，因為您無法將擴充性案例，不是好的理由。 Framework 使用者想要基於各種 nonobvious 原因的詳細資訊，例如新增方便成員繼承自類別。 請參閱[非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)nonobvious 原因，例如使用者想要繼承自型別。  
  
 很好的理由，用於密封類別包括下列各項：  
  
-   類別是靜態類別。 請參閱[靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)。  
  
-   此類別會繼承的 protected 成員中儲存安全性敏感密碼。  
  
-   類別繼承許多虛擬成員，而且個別密封它們的成本會超過保留的未密封的類別的優點。  
  
-   此類別是需要非常快速的執行階段查閱的屬性。 密封的屬性會有較高的效能層級，於未密封的。 請參閱[屬性](../../../docs/standard/design-guidelines/attributes.md)。  
  
 **X DO NOT** 在密封類型上宣告受保護或虛擬的成員。  
  
 根據定義，密封的類型無法繼承自。 這表示無法呼叫密封類型上的受保護的成員，而且不能覆寫虛擬方法，密封類型上。  
  
 **✓ CONSIDER** 密封您覆寫的成員。  
  
 可能是因為引進虛擬成員的問題 (所述[虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)) 套用至覆寫，雖然到稍微較低的程度。 密封覆寫保護您抵禦繼承階層架構中的該點開始這些問題。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)

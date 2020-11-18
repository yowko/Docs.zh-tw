---
title: 密封
ms.date: 10/22/2008
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: 29023ad431f9d05caf44e59f66eccee24bfa0433
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828682"
---
# <a name="sealing"></a>密封
物件導向架構的其中一項功能，就是開發人員可以使用架構設計工具無法預期的方式來擴充和自訂它們。 這是可延伸設計的強大功能和風險。 當您設計您的架構時，請務必在需要時仔細設計擴充性，並且在具風險時限制擴充性。

 防止擴充性的強大機制是密封的。 您可以密封類別或個別成員。 密封類別可防止使用者繼承自類別。 密封成員可以防止使用者覆寫特定的成員。

 ❌ 請勿密封類別，而不會有很好的理由。

 密封類別是因為您不能認為擴充性案例不是好的原因。 基於各種 nonobvious 的原因（例如新增便利性成員），需要繼承類別的架構使用者。 請參閱未 [密封的類別](unsealed-classes.md) ，以取得使用者想要從類型繼承的 nonobvious 原因範例。

 密封類別的好理由包括下列各項：

- 類別是靜態類別。 請參閱 [靜態類別設計](static-class.md)。

- 類別會在繼承的受保護成員中儲存安全性機密秘密。

- 類別會繼承許多虛擬成員，而個別密封這些成員的成本，會超過將類別保持未密封的優點。

- 類別是需要非常快速的執行時間查閱的屬性。 密封的屬性比未密封的屬性具有些許較高的效能層級。 請參閱 [屬性](attributes.md)。

 ❌ 請勿在密封類型上宣告受保護的或虛擬成員。

 根據定義，密封類型無法繼承自。 這表示無法呼叫密封型別上的 protected 成員，也無法覆寫密封類型上的虛擬方法。

 ✔️考慮密封您覆寫的成員。

  (在 [虛擬成員](virtual-members.md) 中討論的虛擬成員引進的問題，也) 也適用于覆寫，不過稍微較低的程度。 密封覆寫會防止這些問題從繼承階層中的那個點開始。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [擴充性設計](designing-for-extensibility.md)
- [未密封的類別](unsealed-classes.md)

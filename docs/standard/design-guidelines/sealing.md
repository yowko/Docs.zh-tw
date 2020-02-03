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
ms.openlocfilehash: ddf463e98fb6a9c5ccaae90e9cfc74b5691b13a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743620"
---
# <a name="sealing"></a>密封
物件導向架構的其中一項功能，就是開發人員可以利用 framework 設計工具無法預期的方式來擴充和自訂它們。 這同時也是可擴充設計的威力和危險。 當您設計架構時，請務必仔細設計所需的擴充性，並在危險時限制擴充性。

 防止擴充性的強大機制是密封的。 您可以密封類別或個別成員。 密封類別可防止使用者繼承類別。 密封成員可防止使用者覆寫特定成員。

 ❌ 不要密封類別，而不需要有良好的理由。

 密封類別是因為您不能認為擴充性案例並不是個好理由。 架構使用者想要從類別繼承，以因應各種 nonobvious 的原因，例如加入方便的成員。 如需使用者想要從類型繼承的 nonobvious 原因範例，請參閱未[密封的類別](../../../docs/standard/design-guidelines/unsealed-classes.md)。

 密封類別的好理由包括下列各項：

- 類別是靜態類別。 請參閱[靜態類別設計](../../../docs/standard/design-guidelines/static-class.md)。

- 類別會將安全性機密的秘密儲存在繼承的受保護成員中。

- 類別會繼承許多虛擬成員，而將其個別密封的成本，會超過讓類別不密封的優點。

- 類別是需要非常快速的執行時間查閱的屬性。 密封屬性的效能層級比未密封的屬性稍微高得多。 請參閱[屬性](../../../docs/standard/design-guidelines/attributes.md)。

 ❌ 不要在密封類型上宣告 protected 或 virtual 成員。

 根據定義，密封類型無法繼承自。 這表示不能呼叫密封類型上的 protected 成員，也無法覆寫密封類型上的虛擬方法。

 ✔️請考慮密封您覆寫的成員。

 導入虛擬成員（在[虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)中討論）的問題也適用于覆寫，雖然是稍微較低的程度。 密封覆寫會在繼承階層中從該點開始，讓您免于發生這些問題。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)

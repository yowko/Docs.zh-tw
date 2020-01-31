---
title: 巢狀類型
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: dd13116b13ac8e2d7a3af6ef014eb4f393909515
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743695"
---
# <a name="nested-types"></a>巢狀類型
巢狀型別是在另一個類型的範圍內定義的類型，稱為封入類型。 巢狀型別可以存取其封入類型的所有成員。 例如，它可以存取在封入類型中定義的私用欄位，以及包含在封入類型的所有祖先中所定義的受保護欄位。

 一般而言，應該謹慎使用巢狀型別。 這有幾個原因。 有些開發人員並不完全熟悉此概念。 例如，這些開發人員可能會遇到宣告巢狀型別變數的語法問題。 巢狀型別也非常緊密結合其封入類型，因此不適合做為一般用途的類型。

 巢狀型別最適合用來建立其封入類型的模型化執行詳細資料。 使用者應該不需要宣告巢狀型別的變數，而且幾乎不應該有明確具現化巢狀型別的情況。 例如，集合的列舉值可以是該集合的巢狀型別。 列舉值通常是由其封入類型具現化，而且因為許多語言都支援 foreach 語句，所以一般使用者不需要宣告枚舉器變數。

 當嵌套型別與其外部型別之間的關聯性時，✔️確實使用巢狀型別，因此需要成員協助工具的語法。

 ❌ 不要使用公用的巢狀型別做為邏輯群組結構;針對此使用命名空間。

 ❌ 避免公開公開的巢狀型別。 唯一的例外是，如果嵌套型別的變數只需要在罕見案例（例如子類別化或其他 advanced 自訂案例）中宣告。

 如果類型可能會在包含類型之外參考，❌ 不使用巢狀型別。

 例如，傳遞至在類別上定義之方法的列舉，不應定義為類別中的巢狀型別。

 如果 ❌ 必須由用戶端程式代碼具現化，則不使用巢狀型別。  如果類型具有公用的函式，則可能不會進行嵌套。

 如果類型可以具現化，似乎表示類型本身在架構中有一個位置（您可以建立它、使用它，並在不使用外部類型的情況下摧毀它），因此不應該進行嵌套。 內部類型不應廣泛地在外部類型之外重複使用，而不需要與外部類型有任何關聯性。

 ❌ 不會將嵌套型別定義為介面的成員。 許多語言都不支援這種結構。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)

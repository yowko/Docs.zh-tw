---
title: 巢狀類型
ms.date: 10/22/2008
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: 1ac2f9f5e10149027b79cd67e5077ec6bc17f9c9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820809"
---
# <a name="nested-types"></a>巢狀類型
巢狀型別是在另一個類型的範圍內定義的類型，稱為封入類型。 巢狀型別可以存取其封入類型的所有成員。 例如，它可以存取在封入型別中定義的私用欄位，以及在封入類型的所有祖先中定義之受保護欄位的存取權。

 一般情況下，應該謹慎使用巢狀型別。 這有幾個原因。 有些開發人員並沒有完全熟悉此概念。 例如，這些開發人員可能會遇到宣告巢狀型別變數的語法問題。 巢狀型別也與它們的封入型別緊密結合，因此不適合做為一般用途類型。

 巢狀型別最適合用於模型化其封入類型的執行詳細資料。 使用者應該很少需要宣告巢狀型別的變數，而且幾乎不需要明確地具現化巢狀型別。 例如，集合的列舉值可以是該集合的巢狀型別。 列舉值通常是由其封入型別具現化，而且因為許多語言都支援 foreach 語句，所以列舉值變數很少必須由使用者宣告。

 當嵌套型別與其外部型別之間的關聯性，因此需要有成員協助工具的語法時，✔️確實使用巢狀型別。

 ❌ 請勿使用公用巢狀型別作為邏輯群組結構;針對此使用命名空間。

 ❌ 避免公開公開的巢狀型別。 唯一的例外是，如果只有在罕見的情況下（例如子類別化或其他自訂的自訂案例），才需要宣告巢狀型別的變數。

 ❌ 如果類型很可能在包含類型之外參考，請不要使用巢狀型別。

 例如，傳遞至類別上所定義之方法的列舉不應定義為類別中的巢狀型別。

 ❌ 如果必須由用戶端程式代碼具現化，請勿使用巢狀型別。  如果型別具有公用的函式，它應該不會被嵌套。

 如果型別可以具現化，這似乎會指出型別在架構中有一個位置 (您可以建立它、使用它，並在不使用外部型別) 的情況下終結它，因此不應該進行嵌套。 內部類型不應該廣泛地重複使用於外部類型之外，而不需要任何與外部類型的關聯性。

 ❌ 請勿將巢狀型別定義為介面的成員。 許多語言都不支援這種結構。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [型別設計方針](type.md)
- [架構設計指導方針](index.md)

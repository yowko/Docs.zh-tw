---
title: 相等運算子
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 85a9e81d28995229e6b47d7fe4d0b541265999f8
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821342"
---
# <a name="equality-operators"></a>相等運算子
本節討論多載等號比較運算子，並參考 `operator==` 和 `operator!=` 做為等號比較運算子。

 ❌ 請勿多載其中一個等號比較運算子，而不是另一個相等運算子。

 ✔️確定 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和等號比較運算子具有完全相同的語義和類似的效能特性。

 這通常表示 `Object.Equals` 當相等運算子超載時，需要覆寫。

 ❌ 避免從相等運算子擲回例外狀況。

 例如，如果其中一個引數為 null，而不是擲回，則傳回 false `NullReferenceException` 。

## <a name="equality-operators-on-value-types"></a>實數值型別上的等號比較運算子
 如果等號比較有意義，✔️會在實數值型別上多載等號比較運算子。

 在大部分的程式設計語言中，實數值型別沒有的預設實 `operator==` 值。

## <a name="equality-operators-on-reference-types"></a>參考型別上的等號比較運算子
 ❌ 避免可變參考型別上的多載等號比較運算子。

 許多語言都有參考型別的內建等號比較運算子。 內建運算子通常會實作為參考相等，而許多開發人員會在預設行為變更為值相等時感到驚訝。

 因為不變的參考型別會讓不變的參考型別變得更容易，所以不需要注意參考相等和值相等之間的差異。

 ❌ 如果實作為參考型別的多載等號比較運算子，請避免在參考型別上多載相等運算子。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [使用指導方針](usage-guidelines.md)

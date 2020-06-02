---
title: 相等運算子
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: bd36b98af25db2921c164ac359188997d379a270
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280046"
---
# <a name="equality-operators"></a>相等運算子
本節討論多載等號比較運算子，並將 `operator==` 和 `operator!=` 視為等號比較運算子。

 ❌請勿多載其中一個等號比較運算子，而不是另一個。

 ✔️確實確保 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和等號比較運算子具有完全相同的語義和類似的效能特性。

 這通常表示 `Object.Equals` 當等號比較運算子多載時，必須覆寫。

 ❌避免從等號比較運算子擲回例外狀況。

 例如，如果其中一個引數是 null，而不是擲回，則會傳回 false `NullReferenceException` 。

## <a name="equality-operators-on-value-types"></a>實數值型別的等號比較運算子
 ✔️在實數值型別上多載等號比較運算子（如果相等）是否有意義。

 在大部分的程式設計語言中，實數值型別沒有的預設執行 `operator==` 。

## <a name="equality-operators-on-reference-types"></a>參考型別上的等號比較運算子
 ❌避免可變參考型別的多載等號比較運算子。

 許多語言都有參考型別的內建等號比較運算子。 內建運算子通常會實作為參考相等，而當預設行為變更為值相等時，許多開發人員會感到驚訝。

 不變的參考型別會降低這個問題，因為不可變性會讓您更難注意參考相等和值相等之間的差異。

 ❌避免在參考型別上多載等號比較運算子，但如果執行速度明顯比參考相等

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [使用指導方針](usage-guidelines.md)

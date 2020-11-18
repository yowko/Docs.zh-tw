---
title: 類型設計方針
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 56b4cb6e93cd44c42fbc2921c9ecfd947c304b3b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828539"
---
# <a name="type-design-guidelines"></a>類型設計方針
從 CLR 的觀點來看，只有兩種類別的型別（參考型別和實值型別），但為了討論架構設計，我們將類型分成更多邏輯群組，每個都有自己的特定設計規則。

 類別是參考型別的一般案例。 它們會構成大部分架構中的大量類型。 類別會對其支援的一組豐富的物件導向功能，以及其一般適用性，提供其最普及的程度。 基類和抽象類別是與擴充性相關的特殊邏輯群組。

 介面是可由參考型別和實值型別實作為的型別。 因此，它們可以作為參考型別和實數值型別之多型階層的根。 此外，介面可以用來模擬多個繼承，CLR 本身並不支援。

 結構是實值型別的一般案例，應該保留給小型的簡單型別，類似于語言基本類型。

 列舉是實數值型別的特殊案例，用來定義簡短的值集，例如星期幾、主控台色彩等等。

 靜態類別是要作為靜態成員容器的類型。 它們通常用來提供其他作業的快捷方式。

 委派、例外狀況、屬性、陣列和集合都是適用于特定用途之參考型別的特殊案例，而其設計和使用方式的指導方針會在本書的其他地方討論。

 ✔️確定每個類型都是一組定義完善的相關成員，而不只是隨機的不相關功能集合。

## <a name="in-this-section"></a>本節內容
 [在類別和結構](choosing-between-class-and-struct.md)[抽象類別](abstract-class.md)之間進行選擇設計 [靜態類別設計](static-class.md)[介面設計](interface.md)[結構設計結構](struct.md)設計 [列舉設計](enum.md)[巢狀型別](nested-types.md)*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)

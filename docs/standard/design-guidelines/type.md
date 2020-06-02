---
title: 類型設計方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 17bd300277a039818a3d563c8f2d5f99eb2fc68d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289560"
---
# <a name="type-design-guidelines"></a>類型設計方針
從 CLR 的觀點來看，只有兩種類別的類型（參考型別和實數值型別），但針對架構設計的討論，我們會將類型分成更多的邏輯群組，每個都有自己的特定設計規則。

 類別是參考型別的一般案例。 它們會構成大部分架構中的大量類型。 類別對於其支援的一組豐富物件導向功能，以及其一般適用性，都欠其最熱門。 基類和抽象類別是與擴充性相關的特殊邏輯群組。

 介面是可同時由參考型別和實數值型別來執行的類型。 因此，它們可以當做參考型別和實數值型別之多型階層的根。 此外，介面可以用來模擬多重繼承，CLR 原本並不支援。

 結構是實值型別的一般案例，應保留給小型的簡單型別，類似于語言基本類型。

 列舉是實數值型別的特殊案例，用來定義一組簡短的值，例如一周中的天數、主控台色彩等等。

 靜態類別是要作為靜態成員容器的類型。 它們通常用來提供其他作業的快捷方式。

 委派、例外狀況、屬性、陣列和集合都是適用于特定用途之參考型別的特殊案例，而在本書的其他地方會討論其設計和使用方式的指導方針。

 ✔️確實確保每種類型都是一組定義完善的相關成員，而不只是隨機收集不相關的功能。

## <a name="in-this-section"></a>本節內容
 [選擇類別和結構](choosing-between-class-and-struct.md)[抽象類別設計](abstract-class.md)[靜態類別設計](static-class.md)[介面設計](interface.md)[結構設計](struct.md)[列舉設計](enum.md)[巢狀型別](nested-types.md)*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)

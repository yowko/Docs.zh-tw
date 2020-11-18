---
title: 靜態類別設計
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: efa5ca6e7b5e7b7d03cbe1d55471a388f3faab37
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828656"
---
# <a name="static-class-design"></a>靜態類別設計
靜態類別定義為只包含靜態成員的類別 (當然，除了繼承自的實例成員 <xref:System.Object?displayProperty=nameWithType> ，以及可能) 私用的函式。 某些語言提供靜態類別的內建支援。 在 c # 2.0 和更新版本中，當類別宣告為靜態時，它會是密封的、抽象的，且不能覆寫或宣告任何實例成員。

 靜態類別是純物件導向設計和簡單性之間的折衷。 它們通常用來提供其他作業的快捷方式 (例如 <xref:System.IO.File?displayProperty=nameWithType>) 、擴充方法的持有者，或完整物件導向包裝函式所預期的功能 (例如 <xref:System.Environment?displayProperty=nameWithType>) 。

 ✔️請謹慎使用靜態類別。

 靜態類別只能做為架構之物件導向核心的支援類別使用。

 ❌ 請勿將靜態類別視為其他值區。

 ❌ 請勿在靜態類別中宣告或覆寫實例成員。

 如果您的程式設計語言沒有靜態類別的內建支援，則✔️會將靜態類別宣告為 sealed、abstract，然後新增私用實例的函式。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [型別設計方針](type.md)
- [架構設計指導方針](index.md)

---
title: Protected 成員
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 3cc2ab3e605cfb5382f107dead0c95495858fc6b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828721"
---
# <a name="protected-members"></a>Protected 成員
受保護的成員本身不提供任何擴充性，但它們可以透過子類別化更強大的功能來進行擴充性。 它們可用來公開最先進的自訂選項，而不需要將主要公用介面複雜化。

 架構設計人員必須小心使用受保護的成員，因為「受保護」的名稱可能會提供錯誤的安全性意義。 任何人都可以將未密封的類別子類別化，並存取受保護的成員，因此公用成員所使用的所有相同防禦程式碼撰寫實務都會套用至受保護的成員。

 ✔️考慮使用受保護的成員進行自訂。

 ✔️會將未密封類別中受保護的成員視為公用，以做為安全性、檔和相容性分析的目的。

 任何人都可以從類別繼承，並存取受保護的成員。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [擴充性設計](designing-for-extensibility.md)

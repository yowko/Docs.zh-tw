---
title: 虛擬成員
ms.date: 10/22/2008
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 22eb71ccfc1b9a3d359b0453e4ff47f3f41827f5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828396"
---
# <a name="virtual-members"></a>虛擬成員
您可以覆寫虛擬成員，進而變更子類別的行為。 它們在提供的擴充性方面相當類似回呼，但它們在執行效能和記憶體耗用量方面更好。 此外，在需要建立特殊種類的現有類型 (特製化) 的案例中，虛擬成員會覺得更自然。

 虛擬成員的執行效能優於回呼和事件，但效能不如非虛擬方法更好。

 虛擬成員的主要缺點是，只有在編譯時才能修改虛擬成員的行為。 回呼的行為可在執行時間修改。

 虛擬成員（像是回呼 (以及可能超過回呼) ）在設計、測試和維護方面很昂貴，因為對虛擬成員的任何呼叫都可以無法預期地覆寫，而且可以執行任意程式碼。 此外，通常需要更多投入時間才能清楚定義虛擬成員的合約，因此設計和記錄這些成員的成本較高。

 ❌ 除非您有充分的理由，才能讓成員成為虛擬的，而且您知道設計、測試和維護虛擬成員的所有相關成本。

 虛擬成員在變更方面較不容許，因為它們可以在不中斷相容性的情況下進行變更。 此外，它們的速度會比非虛擬成員還要慢，因為虛擬成員的呼叫不是內嵌的。

 ✔️考慮將擴充性限制為僅限絕對必要。

 ✔️在虛擬成員的公用存取範圍上，偏好受保護的存取範圍。 如果需要) 呼叫受保護的虛擬成員，則公用成員應提供擴充性 (。

 類別的公用成員應為該類別的直接取用者提供正確的一組功能。 虛擬成員是設計用來在子類別中覆寫，而受保護的存取範圍是將所有虛擬擴充功能的範圍設為可使用的最佳方式。

 *部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [擴充性設計](designing-for-extensibility.md)

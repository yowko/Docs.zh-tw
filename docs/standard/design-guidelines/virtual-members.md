---
title: 虛擬成員
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 918208bb44f84988b7fe903c589e82c7bf1f59e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620764"
---
# <a name="virtual-members"></a>虛擬成員
可以覆寫虛擬成員，因此變更子類別的行為。 它們在其提供的擴充性方面相當類似回呼，但它們在執行效能和記憶體耗用量方面比較好。 此外，在需要建立一種特殊類型（特製化）的案例中，虛擬成員的外觀更為自然。

 虛擬成員的執行效果優於回呼和事件，但不會比非虛擬方法執行得好。

 虛擬成員的主要缺點在於，虛擬成員的行為只能在編譯時進行修改。 您可以在執行時間修改回呼的行為。

 像回呼（也可能是回呼）等虛擬成員的設計、測試和維護成本高昂，因為對虛擬成員的任何呼叫都可以在無法預期的情況下遭到覆寫，而且可以執行任意程式碼。 此外，通常需要更多的工作來清楚定義虛擬成員的合約，因此設計和記錄它們的成本會更高。

 ❌除非您有很好的理由要這麼做，否則請不要將成員設為虛擬，而且您會瞭解與設計、測試和維護虛擬成員相關的所有成本。

 在不中斷相容性的情況下，虛擬成員可以對其進行變更，而不會有太大的容許。 此外，它們的速度會比非虛擬成員慢，主要是因為不會內嵌對虛擬成員的呼叫。

 ✔️考慮限制只有絕對必要的擴充性。

 ✔️偏好透過虛擬成員的公用存取範圍來保護存取範圍。 公用成員應該藉由呼叫受保護的虛擬成員來提供擴充性（如有需要）。

 類別的公用成員應該為該類別的直接取用者提供正確的功能集。 虛擬成員是設計用來在子類別中覆寫，而受保護的存取範圍是將所有虛擬擴充點限定于其使用位置的絕佳方式。

 *部分 &copy; 2005，2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [擴充性設計](designing-for-extensibility.md)

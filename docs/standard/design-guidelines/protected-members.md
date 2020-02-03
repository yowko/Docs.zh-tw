---
title: Protected 成員
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 44d342662e1aaeb51f14470f354f2dadd9a6f18d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743652"
---
# <a name="protected-members"></a><span data-ttu-id="a6d7e-102">Protected 成員</span><span class="sxs-lookup"><span data-stu-id="a6d7e-102">Protected Members</span></span>
<span data-ttu-id="a6d7e-103">受保護成員本身並不提供任何擴充性，但可以透過子類別化更強大的方式進行擴充性。</span><span class="sxs-lookup"><span data-stu-id="a6d7e-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="a6d7e-104">它們可用來公開先進的自訂選項，而不會不必要地使主要公用介面複雜化。</span><span class="sxs-lookup"><span data-stu-id="a6d7e-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="a6d7e-105">架構設計人員必須謹慎使用受保護的成員，因為「受保護」的名稱可能會提供不安全的安全性意義。</span><span class="sxs-lookup"><span data-stu-id="a6d7e-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="a6d7e-106">任何人都可以將未密封的類別子類別化，並存取受保護的成員，因此，公用成員所使用的所有相同的防禦性編碼做法都適用于受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="a6d7e-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="a6d7e-107">✔️考慮使用受保護的成員進行 advanced 自訂。</span><span class="sxs-lookup"><span data-stu-id="a6d7e-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="a6d7e-108">✔️會將未密封類別中的受保護成員視為公用，以做為安全性、檔和相容性分析的目的。</span><span class="sxs-lookup"><span data-stu-id="a6d7e-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="a6d7e-109">任何人都可以繼承自類別，並存取受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="a6d7e-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="a6d7e-110">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="a6d7e-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a6d7e-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="a6d7e-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a6d7e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d7e-112">See also</span></span>

- [<span data-ttu-id="a6d7e-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="a6d7e-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="a6d7e-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="a6d7e-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)

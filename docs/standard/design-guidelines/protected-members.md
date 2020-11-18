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
# <a name="protected-members"></a><span data-ttu-id="f1a65-102">Protected 成員</span><span class="sxs-lookup"><span data-stu-id="f1a65-102">Protected Members</span></span>
<span data-ttu-id="f1a65-103">受保護的成員本身不提供任何擴充性，但它們可以透過子類別化更強大的功能來進行擴充性。</span><span class="sxs-lookup"><span data-stu-id="f1a65-103">Protected members by themselves do not provide any extensibility, but they can make extensibility through subclassing more powerful.</span></span> <span data-ttu-id="f1a65-104">它們可用來公開最先進的自訂選項，而不需要將主要公用介面複雜化。</span><span class="sxs-lookup"><span data-stu-id="f1a65-104">They can be used to expose advanced customization options without unnecessarily complicating the main public interface.</span></span>

 <span data-ttu-id="f1a65-105">架構設計人員必須小心使用受保護的成員，因為「受保護」的名稱可能會提供錯誤的安全性意義。</span><span class="sxs-lookup"><span data-stu-id="f1a65-105">Framework designers need to be careful with protected members because the name "protected" can give a false sense of security.</span></span> <span data-ttu-id="f1a65-106">任何人都可以將未密封的類別子類別化，並存取受保護的成員，因此公用成員所使用的所有相同防禦程式碼撰寫實務都會套用至受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="f1a65-106">Anyone is able to subclass an unsealed class and access protected members, and so all the same defensive coding practices used for public members apply to protected members.</span></span>

 <span data-ttu-id="f1a65-107">✔️考慮使用受保護的成員進行自訂。</span><span class="sxs-lookup"><span data-stu-id="f1a65-107">✔️ CONSIDER using protected members for advanced customization.</span></span>

 <span data-ttu-id="f1a65-108">✔️會將未密封類別中受保護的成員視為公用，以做為安全性、檔和相容性分析的目的。</span><span class="sxs-lookup"><span data-stu-id="f1a65-108">✔️ DO treat protected members in unsealed classes as public for the purpose of security, documentation, and compatibility analysis.</span></span>

 <span data-ttu-id="f1a65-109">任何人都可以從類別繼承，並存取受保護的成員。</span><span class="sxs-lookup"><span data-stu-id="f1a65-109">Anyone can inherit from a class and access the protected members.</span></span>

 <span data-ttu-id="f1a65-110">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="f1a65-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f1a65-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="f1a65-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f1a65-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="f1a65-112">See also</span></span>

- [<span data-ttu-id="f1a65-113">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="f1a65-113">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="f1a65-114">擴充性設計</span><span class="sxs-lookup"><span data-stu-id="f1a65-114">Designing for Extensibility</span></span>](designing-for-extensibility.md)

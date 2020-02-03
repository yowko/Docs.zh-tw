---
title: 命名參數
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: ebe2e2db4b109057bf576d4e18cfe511c657707e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743824"
---
# <a name="naming-parameters"></a><span data-ttu-id="b24ce-102">命名參數</span><span class="sxs-lookup"><span data-stu-id="b24ce-102">Naming Parameters</span></span>
<span data-ttu-id="b24ce-103">除了可讀性的明顯原因之外，請務必遵循參數名稱的指導方針，因為當視覺化設計工具提供 Intellisense 和類別流覽功能時，參數會顯示在檔和設計師中。</span><span class="sxs-lookup"><span data-stu-id="b24ce-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="b24ce-104">✔️請在參數名稱中使用 camelCasing。</span><span class="sxs-lookup"><span data-stu-id="b24ce-104">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="b24ce-105">✔️確實使用描述性的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="b24ce-105">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="b24ce-106">✔️考慮根據參數的意義（而非參數的類型）來使用名稱。</span><span class="sxs-lookup"><span data-stu-id="b24ce-106">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="b24ce-107">命名運算子多載參數</span><span class="sxs-lookup"><span data-stu-id="b24ce-107">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="b24ce-108">如果參數沒有任何意義，✔️確實使用二元運算子多載參數名稱的 `left` 和 `right`。</span><span class="sxs-lookup"><span data-stu-id="b24ce-108">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="b24ce-109">如果參數沒有意義，✔️確實使用一元運算子多載參數名稱的 `value`。</span><span class="sxs-lookup"><span data-stu-id="b24ce-109">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="b24ce-110">✔️針對運算子多載參數考慮有意義的名稱，如果這麼做會增加重要的值。</span><span class="sxs-lookup"><span data-stu-id="b24ce-110">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="b24ce-111">❌ 不要針對運算子多載參數名稱使用縮寫或數值索引。</span><span class="sxs-lookup"><span data-stu-id="b24ce-111">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="b24ce-112">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="b24ce-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b24ce-113">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="b24ce-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b24ce-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b24ce-114">See also</span></span>

- [<span data-ttu-id="b24ce-115">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b24ce-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b24ce-116">命名方針</span><span class="sxs-lookup"><span data-stu-id="b24ce-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

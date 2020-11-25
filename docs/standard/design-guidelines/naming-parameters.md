---
title: 命名參數
description: 瞭解參數命名的指導方針。 例如，使用描述性參數名稱 & camel 大小寫，& 考慮根據意義而非類型來命名。
ms.date: 10/22/2008
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 9f03eda511c2ef0c9565d270c52fd72bf54692d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698347"
---
# <a name="naming-parameters"></a><span data-ttu-id="a1ba2-104">命名參數</span><span class="sxs-lookup"><span data-stu-id="a1ba2-104">Naming Parameters</span></span>

<span data-ttu-id="a1ba2-105">除了可讀性的明顯原因之外，請務必遵循參數名稱的指導方針，因為當視覺化設計工具提供 Intellisense 和類別流覽功能時，參數會顯示在檔和設計工具中。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-105">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="a1ba2-106">✔️在參數名稱中使用 >camelcasing。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-106">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="a1ba2-107">✔️請使用描述性參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-107">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="a1ba2-108">✔️考慮依據參數的意義（而非參數的類型）來使用名稱。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-108">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="a1ba2-109">命名運算子多載參數</span><span class="sxs-lookup"><span data-stu-id="a1ba2-109">Naming Operator Overload Parameters</span></span>

 <span data-ttu-id="a1ba2-110">`left`如果沒有任何意義的參數，✔️請使用和 `right` for 二元運算子多載參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-110">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="a1ba2-111">`value`如果沒有任何意義的參數，✔️請使用一元運算子多載參數名稱。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-111">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="a1ba2-112">✔️針對運算子多載參數考慮有意義的名稱，如果這樣做會增加重要的值。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-112">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="a1ba2-113">❌ 請勿針對運算子多載參數名稱使用縮寫或數位索引。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-113">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="a1ba2-114">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="a1ba2-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a1ba2-115">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="a1ba2-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a1ba2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1ba2-116">See also</span></span>

- [<span data-ttu-id="a1ba2-117">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="a1ba2-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="a1ba2-118">命名指導方針</span><span class="sxs-lookup"><span data-stu-id="a1ba2-118">Naming Guidelines</span></span>](naming-guidelines.md)

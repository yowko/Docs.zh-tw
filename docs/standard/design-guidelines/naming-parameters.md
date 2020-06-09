---
title: 命名參數
description: 瞭解參數的命名方針。 例如，使用描述性參數名稱 & camel 大小寫，& 考慮根據意義（而非類型）來命名。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 54f37c4d6a0f9a6931fa69d612bf0e45bf1f2ce7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583514"
---
# <a name="naming-parameters"></a><span data-ttu-id="f62db-104">命名參數</span><span class="sxs-lookup"><span data-stu-id="f62db-104">Naming Parameters</span></span>
<span data-ttu-id="f62db-105">除了可讀性的明顯原因之外，請務必遵循參數名稱的指導方針，因為當視覺化設計工具提供 Intellisense 和類別流覽功能時，參數會顯示在檔和設計師中。</span><span class="sxs-lookup"><span data-stu-id="f62db-105">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="f62db-106">✔️請在參數名稱中使用 camelCasing。</span><span class="sxs-lookup"><span data-stu-id="f62db-106">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="f62db-107">✔️確實使用描述性的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="f62db-107">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="f62db-108">✔️考慮根據參數的意義（而非參數的類型）來使用名稱。</span><span class="sxs-lookup"><span data-stu-id="f62db-108">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="f62db-109">命名運算子多載參數</span><span class="sxs-lookup"><span data-stu-id="f62db-109">Naming Operator Overload Parameters</span></span>
 <span data-ttu-id="f62db-110">`left`如果參數沒有意義，✔️確實使用和 `right` 二元運算子多載參數名稱。</span><span class="sxs-lookup"><span data-stu-id="f62db-110">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="f62db-111">`value`如果參數沒有意義，✔️會使用一元運算子多載參數名稱。</span><span class="sxs-lookup"><span data-stu-id="f62db-111">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="f62db-112">✔️針對運算子多載參數考慮有意義的名稱，如果這麼做會增加重要的值。</span><span class="sxs-lookup"><span data-stu-id="f62db-112">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="f62db-113">❌請勿針對運算子多載參數名稱使用縮寫或數值索引。</span><span class="sxs-lookup"><span data-stu-id="f62db-113">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="f62db-114">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="f62db-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f62db-115">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="f62db-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f62db-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f62db-116">See also</span></span>

- [<span data-ttu-id="f62db-117">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="f62db-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="f62db-118">命名方針</span><span class="sxs-lookup"><span data-stu-id="f62db-118">Naming Guidelines</span></span>](naming-guidelines.md)

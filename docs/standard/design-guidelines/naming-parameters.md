---
title: 命名參數
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 0bb67056bb39b6a5f372191a1d0b0bb0dc1fe4d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709175"
---
# <a name="naming-parameters"></a><span data-ttu-id="f8598-102">命名參數</span><span class="sxs-lookup"><span data-stu-id="f8598-102">Naming Parameters</span></span>
<span data-ttu-id="f8598-103">除了可讀性的明顯原因之外，請務必遵循參數名稱的指導方針，因為當視覺化設計工具提供 Intellisense 和類別流覽功能時，參數會顯示在檔和設計師中。</span><span class="sxs-lookup"><span data-stu-id="f8598-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="f8598-104">**✓ DO**在參數名稱中使用 camelCasing。</span><span class="sxs-lookup"><span data-stu-id="f8598-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="f8598-105">**✓ DO**使用描述性參數名稱。</span><span class="sxs-lookup"><span data-stu-id="f8598-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="f8598-106">**✓請考慮**根據參數的意義（而非參數的類型）來使用名稱。</span><span class="sxs-lookup"><span data-stu-id="f8598-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="f8598-107">命名運算子多載參數</span><span class="sxs-lookup"><span data-stu-id="f8598-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="f8598-108">如果參數沒有意義， **✓**會使用 `left`，並 `right` 二元運算子多載參數名稱。</span><span class="sxs-lookup"><span data-stu-id="f8598-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="f8598-109">如果參數沒有意義，則**✓**會使用一元運算子多載參數名稱 `value`。</span><span class="sxs-lookup"><span data-stu-id="f8598-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="f8598-110">如果這樣做會增加重要的值，✓會針對運算子多載參數**考慮**有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8598-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="f8598-111">**X 不會**針對運算子多載參數名稱使用縮寫或數值索引。</span><span class="sxs-lookup"><span data-stu-id="f8598-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="f8598-112">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="f8598-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f8598-113">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="f8598-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8598-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8598-114">See also</span></span>

- [<span data-ttu-id="f8598-115">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="f8598-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="f8598-116">命名方針</span><span class="sxs-lookup"><span data-stu-id="f8598-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

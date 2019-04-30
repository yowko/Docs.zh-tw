---
title: 命名參數
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 0e5b33839372e303b96bd6b84949f9a82da2f689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026300"
---
# <a name="naming-parameters"></a><span data-ttu-id="d8ba0-102">命名參數</span><span class="sxs-lookup"><span data-stu-id="d8ba0-102">Naming Parameters</span></span>
<span data-ttu-id="d8ba0-103">除了可讀性的明顯原因，請務必遵循的指導方針的參數名稱，因為參數會顯示在文件，並在設計工具中，視覺化設計工具提供 Intellisense 和瀏覽功能的類別時。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="d8ba0-104">**✓ DO** 將 camelCasing 用於參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="d8ba0-105">**✓ DO** 使用描述性的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="d8ba0-106">**✓ CONSIDER** 使用根據參數的意義，而不是參數的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="d8ba0-107">運算子多載參數命名</span><span class="sxs-lookup"><span data-stu-id="d8ba0-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="d8ba0-108">**✓ DO** 使用 `left` 和 `right` 的二元運算子多載參數名稱是否有任何參數的意義。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="d8ba0-109">**✓ DO** 使用 `value` 的一元運算子多載的參數名稱是否有任何參數的意義。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="d8ba0-110">**✓ CONSIDER** 有意義的名稱，如運算子多載參數，如果這樣做會增加重要的值。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="d8ba0-111">**X DO NOT** 使用縮寫或數值索引運算子多載的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="d8ba0-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="d8ba0-112">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="d8ba0-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d8ba0-113">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="d8ba0-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ba0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8ba0-114">See also</span></span>

- [<span data-ttu-id="d8ba0-115">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="d8ba0-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="d8ba0-116">命名方針</span><span class="sxs-lookup"><span data-stu-id="d8ba0-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

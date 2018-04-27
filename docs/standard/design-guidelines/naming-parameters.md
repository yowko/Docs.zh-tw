---
title: 命名參數
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3e5dfe35fd4f2939898acee44764535c6de5fe9e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="naming-parameters"></a><span data-ttu-id="6c54c-102">命名參數</span><span class="sxs-lookup"><span data-stu-id="6c54c-102">Naming Parameters</span></span>
<span data-ttu-id="6c54c-103">超出明顯原因的可讀性，請務必遵循的指導方針的參數名稱，因為參數會顯示在文件和設計工具中，在視覺化設計工具提供 Intellisense 和瀏覽功能的類別。</span><span class="sxs-lookup"><span data-stu-id="6c54c-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="6c54c-104">**✓ 不要**camelCasing 用於參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6c54c-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="6c54c-105">**✓ 不要**使用描述性的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6c54c-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="6c54c-106">**✓ 考慮**使用根據參數的意義，而不是參數的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="6c54c-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="6c54c-107">運算子多載參數命名</span><span class="sxs-lookup"><span data-stu-id="6c54c-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="6c54c-108">**✓ 不要**使用`left`和`right`的二元運算子多載參數名稱是否有任何參數的意義。</span><span class="sxs-lookup"><span data-stu-id="6c54c-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="6c54c-109">**✓ 不要**使用`value`的一元運算子多載的參數名稱是否有任何參數的意義。</span><span class="sxs-lookup"><span data-stu-id="6c54c-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="6c54c-110">**✓ 考慮**有意義的名稱，如運算子多載參數，如果這樣做會增加重要的值。</span><span class="sxs-lookup"><span data-stu-id="6c54c-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="6c54c-111">**X 不**使用縮寫或數值索引運算子多載的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="6c54c-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="6c54c-112">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="6c54c-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6c54c-113">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="6c54c-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c54c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c54c-114">See Also</span></span>  
 [<span data-ttu-id="6c54c-115">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="6c54c-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="6c54c-116">命名方針</span><span class="sxs-lookup"><span data-stu-id="6c54c-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

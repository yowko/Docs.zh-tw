---
title: 命名資源
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5b53fc383e6fc9a5f056bab4eabde9979cd734b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186171"
---
# <a name="naming-resources"></a><span data-ttu-id="d05e5-102">命名資源</span><span class="sxs-lookup"><span data-stu-id="d05e5-102">Naming Resources</span></span>
<span data-ttu-id="d05e5-103">因為可以透過特定的物件參考可當地語系化的資源，如同它們是屬性，就有一個資源的命名方針如下屬性指導方針。</span><span class="sxs-lookup"><span data-stu-id="d05e5-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>  
  
 <span data-ttu-id="d05e5-104">**✓ DO** PascalCasing 用於資源索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d05e5-104">**✓ DO** use PascalCasing in resource keys.</span></span>  
  
 <span data-ttu-id="d05e5-105">**✓ DO** 提供描述性的而不是簡短的識別項。</span><span class="sxs-lookup"><span data-stu-id="d05e5-105">**✓ DO** provide descriptive rather than short identifiers.</span></span>  
  
 <span data-ttu-id="d05e5-106">**X DO NOT** 使用主要的 CLR 語言的語言特有的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d05e5-106">**X DO NOT** use language-specific keywords of the main CLR languages.</span></span>  
  
 <span data-ttu-id="d05e5-107">**✓ DO** 使用只使用英數字元和底線命名資源。</span><span class="sxs-lookup"><span data-stu-id="d05e5-107">**✓ DO** use only alphanumeric characters and underscores in naming resources.</span></span>  
  
 <span data-ttu-id="d05e5-108">**✓ DO** 下列命名慣例用於例外狀況訊息的資源。</span><span class="sxs-lookup"><span data-stu-id="d05e5-108">**✓ DO** use the following naming convention for exception message resources.</span></span>  
  
 <span data-ttu-id="d05e5-109">例外狀況型別名稱再加上例外狀況的簡短識別項，應該使用的資源識別碼：</span><span class="sxs-lookup"><span data-stu-id="d05e5-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 <span data-ttu-id="d05e5-110">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="d05e5-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d05e5-111">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="d05e5-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05e5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d05e5-112">See also</span></span>

- [<span data-ttu-id="d05e5-113">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="d05e5-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="d05e5-114">命名方針</span><span class="sxs-lookup"><span data-stu-id="d05e5-114">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

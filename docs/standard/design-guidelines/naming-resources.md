---
title: 命名資源
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 95aff35569e58eacfd064609140a29b53e0036da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743822"
---
# <a name="naming-resources"></a><span data-ttu-id="cffda-102">命名資源</span><span class="sxs-lookup"><span data-stu-id="cffda-102">Naming Resources</span></span>
<span data-ttu-id="cffda-103">因為可當地語系化的資源可以透過特定物件來參考，如同它們是屬性一樣，資源的命名指導方針類似于屬性方針。</span><span class="sxs-lookup"><span data-stu-id="cffda-103">Because localizable resources can be referenced via certain objects as if they were properties, the naming guidelines for resources are similar to property guidelines.</span></span>

 <span data-ttu-id="cffda-104">✔️在資源金鑰中使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="cffda-104">✔️ DO use PascalCasing in resource keys.</span></span>

 <span data-ttu-id="cffda-105">✔️提供描述性，而不是簡短識別碼。</span><span class="sxs-lookup"><span data-stu-id="cffda-105">✔️ DO provide descriptive rather than short identifiers.</span></span>

 <span data-ttu-id="cffda-106">❌ 不使用主要 CLR 語言的特定語言關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cffda-106">❌ DO NOT use language-specific keywords of the main CLR languages.</span></span>

 <span data-ttu-id="cffda-107">✔️只在命名資源中使用英數位元和底線。</span><span class="sxs-lookup"><span data-stu-id="cffda-107">✔️ DO use only alphanumeric characters and underscores in naming resources.</span></span>

 <span data-ttu-id="cffda-108">✔️針對例外狀況訊息資源，請使用下列命名慣例。</span><span class="sxs-lookup"><span data-stu-id="cffda-108">✔️ DO use the following naming convention for exception message resources.</span></span>

 <span data-ttu-id="cffda-109">資源識別碼應該是例外狀況類型名稱加上例外狀況的簡短識別碼：</span><span class="sxs-lookup"><span data-stu-id="cffda-109">The resource identifier should be the exception type name plus a short identifier of the exception:</span></span>

 <span data-ttu-id="cffda-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span><span class="sxs-lookup"><span data-stu-id="cffda-110">`ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`</span></span>
 `ArgumentExceptionFileNameIsMalformed`

 <span data-ttu-id="cffda-111">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="cffda-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cffda-112">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="cffda-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cffda-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cffda-113">See also</span></span>

- [<span data-ttu-id="cffda-114">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="cffda-114">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="cffda-115">命名方針</span><span class="sxs-lookup"><span data-stu-id="cffda-115">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)

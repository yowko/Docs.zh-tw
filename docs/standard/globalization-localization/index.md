---
title: 全球化與當地語系化 .NET 應用程式
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 501e23656b3a31dc14e0b2213252ef52c598140f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622634"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="52c56-102">全球化與當地語系化 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="52c56-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="52c56-103">開發世界通用的應用程式，包括可以當地語系化為一或多種語言的應用程式，這個開發過程包含三個步驟：全球化、檢閱是否可當地語系化，以及當地語系化。</span><span class="sxs-lookup"><span data-stu-id="52c56-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="52c56-104">全球化</span><span class="sxs-lookup"><span data-stu-id="52c56-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="52c56-105">這個步驟包含設計和撰寫文化特性中性和語言中性的應用程式程式碼，且該應用程式支援當地語系化使用者介面和所有使用者的區域資料。</span><span class="sxs-lookup"><span data-stu-id="52c56-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="52c56-106">這個步驟包含不是根據文化特性假設做出的設計和開發決策。</span><span class="sxs-lookup"><span data-stu-id="52c56-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="52c56-107">即使全球化的應用程式並未當地語系化，但是它的設計和撰寫方式讓後續能夠相對方便地進行一種或多種語言的當地語系化。</span><span class="sxs-lookup"><span data-stu-id="52c56-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="52c56-108">可當地語系化檢閱</span><span class="sxs-lookup"><span data-stu-id="52c56-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="52c56-109">這個步驟包含檢閱應用程式的程式碼和設計，確保它可以輕鬆地當地語系化並識別當地語系化時可能發生的阻礙，以及確認應用程式的可執行碼與其資源分開。</span><span class="sxs-lookup"><span data-stu-id="52c56-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="52c56-110">如果全球化階段有效，則當地語系化能力檢閱將確認全球化期間所選擇的設計和編碼。</span><span class="sxs-lookup"><span data-stu-id="52c56-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="52c56-111">當地語系化能力階段也可能會找出任何其餘的問題，如此應用程式的原始程式碼就不需要在當地語系化階段進行修改。</span><span class="sxs-lookup"><span data-stu-id="52c56-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="52c56-112">當地語系化</span><span class="sxs-lookup"><span data-stu-id="52c56-112">Localization</span></span>](localization.md)

<span data-ttu-id="52c56-113">這個步驟包含自訂特定文化特性或地區的應用程式。</span><span class="sxs-lookup"><span data-stu-id="52c56-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="52c56-114">如果已正確執行全球化和當地語系化能力的步驟，則當地語系化的主要工作就是轉譯使用者介面。</span><span class="sxs-lookup"><span data-stu-id="52c56-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="52c56-115">依照下列三個步驟執行可提供兩項優點：</span><span class="sxs-lookup"><span data-stu-id="52c56-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="52c56-116">您不需要重新設計用於支援單一文化特性 (例如英文 (美國)) 的應用程式，即可支援其他文化特性。</span><span class="sxs-lookup"><span data-stu-id="52c56-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="52c56-117">可產生更穩定且較少 Bug 的當地語系化應用程式。</span><span class="sxs-lookup"><span data-stu-id="52c56-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="52c56-118">.NET 提供各種開發全球通用及當地語系化應用程式的支援。</span><span class="sxs-lookup"><span data-stu-id="52c56-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="52c56-119">特別是，.NET 類別庫中的許多類型成員，會傳回反映目前使用者文化特性或特定文化特性慣例的值，藉以協助全球化。</span><span class="sxs-lookup"><span data-stu-id="52c56-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="52c56-120">此外，.NET 還支援附屬組件，可簡化當地語系化應用程式的程序。</span><span class="sxs-lookup"><span data-stu-id="52c56-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="52c56-121">如需其他資訊，請參閱[全球化文件](/globalization/)。</span><span class="sxs-lookup"><span data-stu-id="52c56-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="52c56-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="52c56-122">In this section</span></span>

[<span data-ttu-id="52c56-123">全球化</span><span class="sxs-lookup"><span data-stu-id="52c56-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="52c56-124">討論建立世界通用應用程式的第一個階段，包括設計和撰寫文化特性中性和語言中性之應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="52c56-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="52c56-125">可當地語系化檢閱</span><span class="sxs-lookup"><span data-stu-id="52c56-125">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="52c56-126">討論建立當地語系化應用程式的第二個階段，包括識別當地語系化過程中可能遭遇到的阻礙。</span><span class="sxs-lookup"><span data-stu-id="52c56-126">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="52c56-127">當地語系化</span><span class="sxs-lookup"><span data-stu-id="52c56-127">Localization</span></span>](localization.md)

<span data-ttu-id="52c56-128">討論建立當地語系化應用程式的最後一個階段，包括自訂特定區域或文化特性的應用程式使用者介面。</span><span class="sxs-lookup"><span data-stu-id="52c56-128">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="52c56-129">不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="52c56-129">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="52c56-130">說明如何使用預設為區分文化特性的 .NET 方法與類別，來取得不區分文化特性的結果。</span><span class="sxs-lookup"><span data-stu-id="52c56-130">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="52c56-131">開發世界性的應用程式的最佳做法</span><span class="sxs-lookup"><span data-stu-id="52c56-131">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="52c56-132">說明進行全球化、當地語系化和開發世界性的 ASP.NET 的最佳實施方針。</span><span class="sxs-lookup"><span data-stu-id="52c56-132">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="52c56-133">參考資料</span><span class="sxs-lookup"><span data-stu-id="52c56-133">Reference</span></span>

- <span data-ttu-id="52c56-134"><xref:System.Globalization?displayProperty=nameWithType> 命名空間</span><span class="sxs-lookup"><span data-stu-id="52c56-134"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="52c56-135">包含類別，定義與文化特性相關的資訊，包括語言、國家/地區、使用中的日曆、日期、貨幣和數字的格式模式，以及字串的排序順序。</span><span class="sxs-lookup"><span data-stu-id="52c56-135">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="52c56-136"><xref:System.Resources> 命名空間</span><span class="sxs-lookup"><span data-stu-id="52c56-136"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="52c56-137">提供建立、管理和使用資源的類別。</span><span class="sxs-lookup"><span data-stu-id="52c56-137">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="52c56-138"><xref:System.Text> 命名空間</span><span class="sxs-lookup"><span data-stu-id="52c56-138"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="52c56-139">包含表示 ASCII、ANSI、Unicode 和其他字元編碼方式的類別。</span><span class="sxs-lookup"><span data-stu-id="52c56-139">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="52c56-140">Resgen.exe (資源檔產生器)</span><span class="sxs-lookup"><span data-stu-id="52c56-140">Resgen.exe (Resource File Generator)</span></span>](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="52c56-141">描述如何使用 Resgen.exe 來轉換 .txt 檔案和 XML 資源格式 (.resx) 檔案到通用語言執行平台二進位資源檔。</span><span class="sxs-lookup"><span data-stu-id="52c56-141">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="52c56-142">Winres.exe (Windows Forms 資源編輯器)</span><span class="sxs-lookup"><span data-stu-id="52c56-142">Winres.exe (Windows Forms Resource Editor)</span></span>](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="52c56-143">描述如何使用 Winres.exe 將 Windows Form 表單當地語系化。</span><span class="sxs-lookup"><span data-stu-id="52c56-143">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>

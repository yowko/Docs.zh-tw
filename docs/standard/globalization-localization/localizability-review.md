---
title: 可當地語系化檢閱
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b19bc78f44781923df6873ccc9720f4605731976
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086501"
---
# <a name="localizability-review"></a><span data-ttu-id="482fb-102">可當地語系化檢閱</span><span class="sxs-lookup"><span data-stu-id="482fb-102">Localizability Review</span></span>
<span data-ttu-id="482fb-103">當地語系化能力審查是準備發行到全球之應用程式開發工作的中繼步驟。</span><span class="sxs-lookup"><span data-stu-id="482fb-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="482fb-104">這個步驟會確認全球化應用程式是否準備好進行當地語系化，以及識別使用者介面中需要特殊處理的任何程式碼或任何方面。</span><span class="sxs-lookup"><span data-stu-id="482fb-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="482fb-105">另外還可協助確保當地語系化過程中，不會在應用程式中造成任何功能上的問題。</span><span class="sxs-lookup"><span data-stu-id="482fb-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="482fb-106">當地語系化能力審查提出的所有問題都獲得解決之後，您的應用程式就可以開始進行當地語系化。</span><span class="sxs-lookup"><span data-stu-id="482fb-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="482fb-107">如果當地語系化能力檢閱相當徹底，您應該不需要在當地語系化過程期間修改任何原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="482fb-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="482fb-108">當地語系化能力審查包括下列三項檢查：</span><span class="sxs-lookup"><span data-stu-id="482fb-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="482fb-109">是否已實作全球化建議？</span><span class="sxs-lookup"><span data-stu-id="482fb-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="482fb-110">是否正確處理區分文化特性的功能？</span><span class="sxs-lookup"><span data-stu-id="482fb-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="482fb-111">是否使用國際資料測試過您的應用程式？</span><span class="sxs-lookup"><span data-stu-id="482fb-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="482fb-112">實作全球化建議</span><span class="sxs-lookup"><span data-stu-id="482fb-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="482fb-113">如果您設計和開發應用程式時已將當地語系化納入考量，而且已遵循[全球化](../../../docs/standard/globalization-localization/globalization.md)一文中所討論的建議，可當地語系化檢閱主要會是一項品質保證的作業。</span><span class="sxs-lookup"><span data-stu-id="482fb-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="482fb-114">否則，在這個階段您應該檢閱並實作[全球化](../../../docs/standard/globalization-localization/globalization.md)的建議，並且修正原始程式碼中造成當地語系化無法順利進行的錯誤。</span><span class="sxs-lookup"><span data-stu-id="482fb-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="482fb-115">處理區分文化特性的功能</span><span class="sxs-lookup"><span data-stu-id="482fb-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="482fb-116">.NET Framework 在一些文化特性差異較大的區域並未提供程式設計方面的支援。</span><span class="sxs-lookup"><span data-stu-id="482fb-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="482fb-117">在大部分情況下，您必須撰寫自訂程式碼來處理下列領域：</span><span class="sxs-lookup"><span data-stu-id="482fb-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="482fb-118">位址。</span><span class="sxs-lookup"><span data-stu-id="482fb-118">Addresses.</span></span>  
  
-   <span data-ttu-id="482fb-119">電話號碼。</span><span class="sxs-lookup"><span data-stu-id="482fb-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="482fb-120">紙張大小。</span><span class="sxs-lookup"><span data-stu-id="482fb-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="482fb-121">用於長度、粗細、面積、容積和溫度的測量單位。</span><span class="sxs-lookup"><span data-stu-id="482fb-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="482fb-122">雖然 .NET Framework 並未提供在測量單位之間進行轉換的內建支援，但是您可以使用 <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> 屬性判斷特定國家或地區是否使用公制，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="482fb-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="482fb-123">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="482fb-123">Testing your application</span></span>  
 <span data-ttu-id="482fb-124">在您將應用程式當地語系化之前，應先使用國際版作業系統上的國際資料進行測試。</span><span class="sxs-lookup"><span data-stu-id="482fb-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="482fb-125">雖然大部分使用者介面此時並不會當地語系化，但是您將能夠偵測出問題所在，如下所示：</span><span class="sxs-lookup"><span data-stu-id="482fb-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="482fb-126">無法跨作業系統版本正確還原序列化的序列化資料。</span><span class="sxs-lookup"><span data-stu-id="482fb-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="482fb-127">未反映目前文化特性慣例的數值資料。</span><span class="sxs-lookup"><span data-stu-id="482fb-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="482fb-128">例如，數字可能採用不正確的群組分隔符號、小數點分隔符號或貨幣符號顯示。</span><span class="sxs-lookup"><span data-stu-id="482fb-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="482fb-129">未反映目前文化特性慣例的日期和時間資料。</span><span class="sxs-lookup"><span data-stu-id="482fb-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="482fb-130">例如，表示月份和日期的數字可能以不正確的順序出現、日期分隔符號可能不正確，或是時區資訊可能不正確。</span><span class="sxs-lookup"><span data-stu-id="482fb-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="482fb-131">找不到資源，因為您尚未識別應用程式的預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="482fb-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="482fb-132">特定文化特性的字串以異常的順序顯示。</span><span class="sxs-lookup"><span data-stu-id="482fb-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="482fb-133">傳回未預期結果的字串比較或相等比較。</span><span class="sxs-lookup"><span data-stu-id="482fb-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="482fb-134">如果您已遵循全球化建議開發應用程式、正確地處理區分文化特性的功能，而且找到並解決了測試期間發生的當地語系化問題，就可以繼續進行下一個步驟：[當地語系化](../../../docs/standard/globalization-localization/localization.md)。</span><span class="sxs-lookup"><span data-stu-id="482fb-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="482fb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="482fb-135">See also</span></span>

- [<span data-ttu-id="482fb-136">全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="482fb-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
- [<span data-ttu-id="482fb-137">當地語系化</span><span class="sxs-lookup"><span data-stu-id="482fb-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
- [<span data-ttu-id="482fb-138">全球化</span><span class="sxs-lookup"><span data-stu-id="482fb-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
- [<span data-ttu-id="482fb-139">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="482fb-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)

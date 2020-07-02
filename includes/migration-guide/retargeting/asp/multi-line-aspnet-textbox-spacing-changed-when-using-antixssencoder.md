---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617137"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="87a4e-101">使用 AntiXSSEncoder 時，多行 ASP.Net TextBox 間距已變更</span><span class="sxs-lookup"><span data-stu-id="87a4e-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="87a4e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="87a4e-102">Details</span></span>

<span data-ttu-id="87a4e-103">在 .NET Framework 4.0 中，如果使用 <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>，則會在回傳時，於多行文字方塊的行間插入額外幾行。</span><span class="sxs-lookup"><span data-stu-id="87a4e-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="87a4e-104">在 .NET Framework 4.5 中，不會包含這些額外的分行符號，但前提是 Web 應用程式是以 .NET Framework 4.5 為目標</span><span class="sxs-lookup"><span data-stu-id="87a4e-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="87a4e-105">建議</span><span class="sxs-lookup"><span data-stu-id="87a4e-105">Suggestion</span></span>

<span data-ttu-id="87a4e-106">請注意，重定目標為 .NET Framework 4.5 的 4.0 版 Web 應用程式可能已改善多行文字方塊，不再插入額外的分行符號。</span><span class="sxs-lookup"><span data-stu-id="87a4e-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="87a4e-107">如果不想這麼做，在 .NET Framework 4.5 上執行的應用程式可藉由將目標設為 .NET Framework 4.0 來保留舊版行為。</span><span class="sxs-lookup"><span data-stu-id="87a4e-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="87a4e-108">名稱</span><span class="sxs-lookup"><span data-stu-id="87a4e-108">Name</span></span>    | <span data-ttu-id="87a4e-109">值</span><span class="sxs-lookup"><span data-stu-id="87a4e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="87a4e-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="87a4e-110">Scope</span></span>   | <span data-ttu-id="87a4e-111">Minor</span><span class="sxs-lookup"><span data-stu-id="87a4e-111">Minor</span></span>       |
| <span data-ttu-id="87a4e-112">版本</span><span class="sxs-lookup"><span data-stu-id="87a4e-112">Version</span></span> | <span data-ttu-id="87a4e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="87a4e-113">4.5</span></span>         |
| <span data-ttu-id="87a4e-114">類型</span><span class="sxs-lookup"><span data-stu-id="87a4e-114">Type</span></span>    | <span data-ttu-id="87a4e-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="87a4e-115">Retargeting</span></span> |

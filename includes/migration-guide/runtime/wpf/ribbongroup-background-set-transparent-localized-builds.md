---
ms.openlocfilehash: d6405573e476ce18513938b500041adefbeeef1b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496722"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="b032b-101">RibbonGroup 背景在當地語系化組建中設定為透明</span><span class="sxs-lookup"><span data-stu-id="b032b-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="b032b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b032b-102">Details</span></span>

<span data-ttu-id="b032b-103">當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="b032b-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="b032b-104">此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。</span><span class="sxs-lookup"><span data-stu-id="b032b-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b032b-105">建議</span><span class="sxs-lookup"><span data-stu-id="b032b-105">Suggestion</span></span>

<span data-ttu-id="b032b-106">升級至 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="b032b-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="b032b-107">名稱</span><span class="sxs-lookup"><span data-stu-id="b032b-107">Name</span></span>    | <span data-ttu-id="b032b-108">值</span><span class="sxs-lookup"><span data-stu-id="b032b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b032b-109">範圍</span><span class="sxs-lookup"><span data-stu-id="b032b-109">Scope</span></span>   |<span data-ttu-id="b032b-110">Edge</span><span class="sxs-lookup"><span data-stu-id="b032b-110">Edge</span></span>|
|<span data-ttu-id="b032b-111">版本</span><span class="sxs-lookup"><span data-stu-id="b032b-111">Version</span></span>|<span data-ttu-id="b032b-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="b032b-112">4.6.2</span></span>|
|<span data-ttu-id="b032b-113">類型</span><span class="sxs-lookup"><span data-stu-id="b032b-113">Type</span></span>|<span data-ttu-id="b032b-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="b032b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b032b-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b032b-115">Affected APIs</span></span>

<span data-ttu-id="b032b-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="b032b-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

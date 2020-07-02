---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622342"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="e13d8-101">RibbonGroup 背景在當地語系化組建中設定為透明</span><span class="sxs-lookup"><span data-stu-id="e13d8-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="e13d8-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e13d8-102">Details</span></span>

<span data-ttu-id="e13d8-103">當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="e13d8-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="e13d8-104">此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。</span><span class="sxs-lookup"><span data-stu-id="e13d8-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e13d8-105">建議</span><span class="sxs-lookup"><span data-stu-id="e13d8-105">Suggestion</span></span>

<span data-ttu-id="e13d8-106">升級至 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="e13d8-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="e13d8-107">名稱</span><span class="sxs-lookup"><span data-stu-id="e13d8-107">Name</span></span>    | <span data-ttu-id="e13d8-108">值</span><span class="sxs-lookup"><span data-stu-id="e13d8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e13d8-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e13d8-109">Scope</span></span>   |<span data-ttu-id="e13d8-110">Edge</span><span class="sxs-lookup"><span data-stu-id="e13d8-110">Edge</span></span>|
|<span data-ttu-id="e13d8-111">版本</span><span class="sxs-lookup"><span data-stu-id="e13d8-111">Version</span></span>|<span data-ttu-id="e13d8-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e13d8-112">4.6.2</span></span>|
|<span data-ttu-id="e13d8-113">類型</span><span class="sxs-lookup"><span data-stu-id="e13d8-113">Type</span></span>|<span data-ttu-id="e13d8-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="e13d8-114">Runtime</span></span>|

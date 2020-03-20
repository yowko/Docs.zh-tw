---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802533"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="18a3a-101">RibbonGroup 背景在當地語系化組建中設定為透明</span><span class="sxs-lookup"><span data-stu-id="18a3a-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="18a3a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="18a3a-102">Details</span></span>|<span data-ttu-id="18a3a-103">當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="18a3a-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="18a3a-104">此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。</span><span class="sxs-lookup"><span data-stu-id="18a3a-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="18a3a-105">建議</span><span class="sxs-lookup"><span data-stu-id="18a3a-105">Suggestion</span></span>|<span data-ttu-id="18a3a-106">升級至 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="18a3a-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="18a3a-107">影響範圍</span><span class="sxs-lookup"><span data-stu-id="18a3a-107">Scope</span></span>|<span data-ttu-id="18a3a-108">Edge</span><span class="sxs-lookup"><span data-stu-id="18a3a-108">Edge</span></span>|
|<span data-ttu-id="18a3a-109">版本</span><span class="sxs-lookup"><span data-stu-id="18a3a-109">Version</span></span>|<span data-ttu-id="18a3a-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="18a3a-110">4.6.2</span></span>|
|<span data-ttu-id="18a3a-111">類型</span><span class="sxs-lookup"><span data-stu-id="18a3a-111">Type</span></span>|<span data-ttu-id="18a3a-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="18a3a-112">Runtime</span></span>|

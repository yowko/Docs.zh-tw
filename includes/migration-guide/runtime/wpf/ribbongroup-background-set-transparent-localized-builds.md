---
ms.openlocfilehash: 9500907c6a1ba5b27008dcad4c9b47aef9092106
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802533"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="d5e59-101">RibbonGroup 背景在當地語系化組建中設定為透明</span><span class="sxs-lookup"><span data-stu-id="d5e59-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d5e59-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5e59-102">Details</span></span>|<span data-ttu-id="d5e59-103">當地語系化組建中的 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 背景一律使用透明筆刷繪製，導致不良的 UI 使用體驗。</span><span class="sxs-lookup"><span data-stu-id="d5e59-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="d5e59-104">此問題已在 .NET Framework 4.7 WPF 修正程式中透過更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> 的當地語系化資源來修正，而這可確保已選取正確的筆刷。</span><span class="sxs-lookup"><span data-stu-id="d5e59-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="d5e59-105">建議</span><span class="sxs-lookup"><span data-stu-id="d5e59-105">Suggestion</span></span>|<span data-ttu-id="d5e59-106">升級至 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="d5e59-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="d5e59-107">範圍</span><span class="sxs-lookup"><span data-stu-id="d5e59-107">Scope</span></span>|<span data-ttu-id="d5e59-108">Edge</span><span class="sxs-lookup"><span data-stu-id="d5e59-108">Edge</span></span>|
|<span data-ttu-id="d5e59-109">版本</span><span class="sxs-lookup"><span data-stu-id="d5e59-109">Version</span></span>|<span data-ttu-id="d5e59-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="d5e59-110">4.6.2</span></span>|
|<span data-ttu-id="d5e59-111">類型</span><span class="sxs-lookup"><span data-stu-id="d5e59-111">Type</span></span>|<span data-ttu-id="d5e59-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="d5e59-112">Runtime</span></span>|


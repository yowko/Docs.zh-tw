---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234132"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="9868c-101">WPF 視窗在擴充到單一顯示器之外時呈現而不裁剪</span><span class="sxs-lookup"><span data-stu-id="9868c-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9868c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9868c-102">Details</span></span>|<span data-ttu-id="9868c-103">在 Windows 8 和更新版本中執行的 .NET Framework 4.6 多重監視器案例中，如果視窗擴充到單一顯示畫面之外，可呈現完整視窗而不會將其裁剪。</span><span class="sxs-lookup"><span data-stu-id="9868c-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="9868c-104">這與舊版 .NET Framework 不同，後者會在 WPF 視窗擴充到單一顯示畫面之外時裁剪該視窗。</span><span class="sxs-lookup"><span data-stu-id="9868c-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="9868c-105">建議</span><span class="sxs-lookup"><span data-stu-id="9868c-105">Suggestion</span></span>|<span data-ttu-id="9868c-106">您可以在應用程式組態檔的 <code>&lt;appSettings&gt;</code> 中使用 <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> 項目，或在應用程式啟動時藉由設定 <code>EnableMultiMonitorDisplayClipping</code> 屬性，來明確設定這項行為 (不論是否裁剪)。</span><span class="sxs-lookup"><span data-stu-id="9868c-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="9868c-107">範圍</span><span class="sxs-lookup"><span data-stu-id="9868c-107">Scope</span></span>|<span data-ttu-id="9868c-108">次要</span><span class="sxs-lookup"><span data-stu-id="9868c-108">Minor</span></span>|
|<span data-ttu-id="9868c-109">版本</span><span class="sxs-lookup"><span data-stu-id="9868c-109">Version</span></span>|<span data-ttu-id="9868c-110">4.6</span><span class="sxs-lookup"><span data-stu-id="9868c-110">4.6</span></span>|
|<span data-ttu-id="9868c-111">類型</span><span class="sxs-lookup"><span data-stu-id="9868c-111">Type</span></span>|<span data-ttu-id="9868c-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="9868c-112">Runtime</span></span>|

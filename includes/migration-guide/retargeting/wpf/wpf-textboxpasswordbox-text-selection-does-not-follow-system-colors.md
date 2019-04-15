---
ms.openlocfilehash: 3f88c8b80518aa65c082dc3da2d75b5221dd00f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233926"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="2e7d2-101">WPF 文字方塊/PasswordBox 文字選取範圍不遵循系統色彩</span><span class="sxs-lookup"><span data-stu-id="2e7d2-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2e7d2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2e7d2-102">Details</span></span>|<span data-ttu-id="2e7d2-103">在 .NET Framework 4.7.1 和舊版中，WPF <code>System.Windows.Controls.TextBox</code> 和 <code>System.Windows.Controls.PasswordBox</code> 只能在 Adorner 圖層轉譯文字選取項目。</span><span class="sxs-lookup"><span data-stu-id="2e7d2-103">In .NET Framework 4.7.1 and earlier versions, WPF <code>System.Windows.Controls.TextBox</code> and <code>System.Windows.Controls.PasswordBox</code> could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="2e7d2-104">在某些系統佈景主題中，這會遮擋文字，讓它變得更難讀取。</span><span class="sxs-lookup"><span data-stu-id="2e7d2-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="2e7d2-105">在 .NET Framework 4.7.2 和更新版本中，開發人員可以選擇非 Adorner 型的選取項目轉譯配置來減輕這個問題。</span><span class="sxs-lookup"><span data-stu-id="2e7d2-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>|
|<span data-ttu-id="2e7d2-106">建議</span><span class="sxs-lookup"><span data-stu-id="2e7d2-106">Suggestion</span></span>|<span data-ttu-id="2e7d2-107">想要利用這項變更的開發人員必須適當設定下列 AppContext 旗標。</span><span class="sxs-lookup"><span data-stu-id="2e7d2-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="2e7d2-108">若要利用這項功能，已安裝的 .NET Framework 版本必須是 4.7.2 或更高。若要啟用非 Adorner 型的選取項目，請使用下列 AppContext 旗標。</span><span class="sxs-lookup"><span data-stu-id="2e7d2-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="2e7d2-109">範圍</span><span class="sxs-lookup"><span data-stu-id="2e7d2-109">Scope</span></span>|<span data-ttu-id="2e7d2-110">Edge</span><span class="sxs-lookup"><span data-stu-id="2e7d2-110">Edge</span></span>|
|<span data-ttu-id="2e7d2-111">版本</span><span class="sxs-lookup"><span data-stu-id="2e7d2-111">Version</span></span>|<span data-ttu-id="2e7d2-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="2e7d2-112">4.7.2</span></span>|
|<span data-ttu-id="2e7d2-113">類型</span><span class="sxs-lookup"><span data-stu-id="2e7d2-113">Type</span></span>|<span data-ttu-id="2e7d2-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="2e7d2-114">Retargeting</span></span>|

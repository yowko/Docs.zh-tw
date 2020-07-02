---
ms.openlocfilehash: 7c2e80669d9ef27f87cde9442d8eeab0ee31a524
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614623"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a><span data-ttu-id="3942b-101">WPF 文字方塊/PasswordBox 文字選取範圍不遵循系統色彩</span><span class="sxs-lookup"><span data-stu-id="3942b-101">WPF TextBox/PasswordBox Text Selection Does Not Follow System Colors</span></span>

#### <a name="details"></a><span data-ttu-id="3942b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3942b-102">Details</span></span>

<span data-ttu-id="3942b-103">在 .NET Framework 4.7.1 和舊版中，WPF `System.Windows.Controls.TextBox` 和 `System.Windows.Controls.PasswordBox` 只能在 Adorner 圖層轉譯文字選取項目。</span><span class="sxs-lookup"><span data-stu-id="3942b-103">In .NET Framework 4.7.1 and earlier versions, WPF `System.Windows.Controls.TextBox` and `System.Windows.Controls.PasswordBox` could only render a text selection in the Adorner layer.</span></span> <span data-ttu-id="3942b-104">在某些系統佈景主題中，這會遮擋文字，讓它變得更難讀取。</span><span class="sxs-lookup"><span data-stu-id="3942b-104">In some system themes this would occlude text, making it hard to read.</span></span>  <span data-ttu-id="3942b-105">在 .NET Framework 4.7.2 和更新版本中，開發人員可以選擇非 Adorner 型的選取項目轉譯配置來減輕這個問題。</span><span class="sxs-lookup"><span data-stu-id="3942b-105">In .NET Framework 4.7.2 and later, developers have an option of enabling a non-Adorner-based selection rendering scheme that alleviates this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3942b-106">建議</span><span class="sxs-lookup"><span data-stu-id="3942b-106">Suggestion</span></span>

<span data-ttu-id="3942b-107">想要利用這項變更的開發人員必須適當設定下列 AppContext 旗標。</span><span class="sxs-lookup"><span data-stu-id="3942b-107">A developer who wants to utilize this change must set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="3942b-108">若要利用這項功能，已安裝的 .NET Framework 版本必須是 4.7.2 或更高。若要啟用非 Adorner 型的選取項目，請使用下列 AppContext 旗標。</span><span class="sxs-lookup"><span data-stu-id="3942b-108">To utilize this feature, the installed .NET Framework version must be 4.7.2 or greater.To enabled the non-adorner-based selection, use the following AppContext flag.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="3942b-109">名稱</span><span class="sxs-lookup"><span data-stu-id="3942b-109">Name</span></span>    | <span data-ttu-id="3942b-110">值</span><span class="sxs-lookup"><span data-stu-id="3942b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3942b-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="3942b-111">Scope</span></span>   | <span data-ttu-id="3942b-112">Edge</span><span class="sxs-lookup"><span data-stu-id="3942b-112">Edge</span></span>        |
| <span data-ttu-id="3942b-113">版本</span><span class="sxs-lookup"><span data-stu-id="3942b-113">Version</span></span> | <span data-ttu-id="3942b-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="3942b-114">4.7.2</span></span>       |
| <span data-ttu-id="3942b-115">類型</span><span class="sxs-lookup"><span data-stu-id="3942b-115">Type</span></span>    | <span data-ttu-id="3942b-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="3942b-116">Retargeting</span></span> |

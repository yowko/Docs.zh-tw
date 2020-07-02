---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614583"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a><span data-ttu-id="fa8fd-101">WinForm 的網域 upbutton 和 downbutton 動作現在會同步</span><span class="sxs-lookup"><span data-stu-id="fa8fd-101">WinForm's Domain upbutton and downbutton actions are in sync now</span></span>

#### <a name="details"></a><span data-ttu-id="fa8fd-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fa8fd-102">Details</span></span>

<span data-ttu-id="fa8fd-103">在 .NET Framework 4.7.1 和先前版本中，<xref:System.Windows.Forms.DomainUpDown> 控制項的 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作會在控制項文字存在時予以忽略，因此開發人員必須在控制項上使用 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 動作，才能使用 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作。</span><span class="sxs-lookup"><span data-stu-id="fa8fd-103">In the .NET Framework 4.7.1 and previous versions the <xref:System.Windows.Forms.DomainUpDown> control's <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action is ignored when control text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before using <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="fa8fd-104">從 .NET Framework 4.7.2 開始，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 這兩個動作在此案例中會獨立工作，並保持同步。</span><span class="sxs-lookup"><span data-stu-id="fa8fd-104">Starting with the .NET Framework 4.7.2 both the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions work independently in this scenario and remain in sync.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fa8fd-105">建議</span><span class="sxs-lookup"><span data-stu-id="fa8fd-105">Suggestion</span></span>

<span data-ttu-id="fa8fd-106">為了讓應用程式可受益於這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="fa8fd-106">In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="fa8fd-107">應用程式可以用下列任一種方式受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="fa8fd-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="fa8fd-108">將其重新編譯為以 .NET Framework 4.7.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="fa8fd-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="fa8fd-109">在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。</span><span class="sxs-lookup"><span data-stu-id="fa8fd-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="fa8fd-110">藉由在應用程式組態檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並將它設定為 `false`，選擇退出舊版捲動行為，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fa8fd-110">It opts out of the legacy scrolling behavior by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="fa8fd-111">名稱</span><span class="sxs-lookup"><span data-stu-id="fa8fd-111">Name</span></span>    | <span data-ttu-id="fa8fd-112">值</span><span class="sxs-lookup"><span data-stu-id="fa8fd-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fa8fd-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="fa8fd-113">Scope</span></span>   | <span data-ttu-id="fa8fd-114">Edge</span><span class="sxs-lookup"><span data-stu-id="fa8fd-114">Edge</span></span>        |
| <span data-ttu-id="fa8fd-115">版本</span><span class="sxs-lookup"><span data-stu-id="fa8fd-115">Version</span></span> | <span data-ttu-id="fa8fd-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="fa8fd-116">4.7.2</span></span>       |
| <span data-ttu-id="fa8fd-117">類型</span><span class="sxs-lookup"><span data-stu-id="fa8fd-117">Type</span></span>    | <span data-ttu-id="fa8fd-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="fa8fd-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fa8fd-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fa8fd-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>

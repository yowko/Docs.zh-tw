---
ms.openlocfilehash: 53ded5ae6e5a025fc7992da099c3481587bb6f31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614578"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a><span data-ttu-id="fc7a4-101">PrivateFontCollection.AddFontFile 方法會釋放字型資源</span><span class="sxs-lookup"><span data-stu-id="fc7a4-101">PrivateFontCollection.AddFontFile method releases Font resources</span></span>

#### <a name="details"></a><span data-ttu-id="fc7a4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fc7a4-102">Details</span></span>

<span data-ttu-id="fc7a4-103">在 .NET Framework 4.7.1 和舊版本中，如果 <xref:System.Drawing.Font> 物件是使用 <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> 方法新增至這個集合，則 <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> 類別不會在處置物件的 <xref:System.Drawing.Text.PrivateFontCollection> 之後釋放 GDI+ 字型資源。</span><span class="sxs-lookup"><span data-stu-id="fc7a4-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> class does not release the GDI+ font resources after the <xref:System.Drawing.Text.PrivateFontCollection> is disposed for <xref:System.Drawing.Font> objects that are added to this collection using the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> method.</span></span> <span data-ttu-id="fc7a4-104">在 .NET Framework 4.7.2 和更新版本中，<xref:System.Drawing.Text.FontCollection.Dispose%2A> 會釋放已藉由檔案形式新增至集合中的 GDI+ 字型。</span><span class="sxs-lookup"><span data-stu-id="fc7a4-104">In the .NET Framework 4.7.2 and later <xref:System.Drawing.Text.FontCollection.Dispose%2A> releases the GDI+ fonts that were added to the collection as files.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fc7a4-105">建議</span><span class="sxs-lookup"><span data-stu-id="fc7a4-105">Suggestion</span></span>

<span data-ttu-id="fc7a4-106">**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="fc7a4-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="fc7a4-107">應用程式可以用下列任一種方式受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="fc7a4-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="fc7a4-108">將其重新編譯為以 .NET Framework 4.7.2 為目標。</span><span class="sxs-lookup"><span data-stu-id="fc7a4-108">It is recompiled to target the .NET Framework 4.7.2.</span></span> <span data-ttu-id="fc7a4-109">在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。</span><span class="sxs-lookup"><span data-stu-id="fc7a4-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="fc7a4-110">以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並將其設定為 `false`，如下範例所示。</span><span class="sxs-lookup"><span data-stu-id="fc7a4-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

<span data-ttu-id="fc7a4-111">如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版本的行為，則可以明確將此 AppContext 參數設為 `true`，選擇不要釋放字型資源。</span><span class="sxs-lookup"><span data-stu-id="fc7a4-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to not release font resources by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="fc7a4-112">名稱</span><span class="sxs-lookup"><span data-stu-id="fc7a4-112">Name</span></span>    | <span data-ttu-id="fc7a4-113">值</span><span class="sxs-lookup"><span data-stu-id="fc7a4-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fc7a4-114">影響範圍</span><span class="sxs-lookup"><span data-stu-id="fc7a4-114">Scope</span></span>   | <span data-ttu-id="fc7a4-115">Edge</span><span class="sxs-lookup"><span data-stu-id="fc7a4-115">Edge</span></span>        |
| <span data-ttu-id="fc7a4-116">版本</span><span class="sxs-lookup"><span data-stu-id="fc7a4-116">Version</span></span> | <span data-ttu-id="fc7a4-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="fc7a4-117">4.7.2</span></span>       |
| <span data-ttu-id="fc7a4-118">類型</span><span class="sxs-lookup"><span data-stu-id="fc7a4-118">Type</span></span>    | <span data-ttu-id="fc7a4-119">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="fc7a4-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="fc7a4-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="fc7a4-120">Affected APIs</span></span>

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>

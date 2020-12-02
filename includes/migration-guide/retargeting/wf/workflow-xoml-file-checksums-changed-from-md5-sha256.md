---
ms.openlocfilehash: b1910bf0338bccd77ad9e983990d4d193698ec1f
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477331"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="1693f-101">工作流程 XOML 檔案總和檢查碼已從 MD5 變更為 SHA256</span><span class="sxs-lookup"><span data-stu-id="1693f-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="1693f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1693f-102">Details</span></span>

<span data-ttu-id="1693f-103">為了支援搭配 Visual Studio 偵錯 XOML 式的工作流程，建置包含 XOML 檔案的工作流程專案時，XOML 檔案內容的總和檢查碼會作為 <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> 值包含在所產生程式碼中。</span><span class="sxs-lookup"><span data-stu-id="1693f-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="1693f-104">在 .NET Framework 4.7.2 及更早版本中，這個總和檢查碼雜湊會使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。</span><span class="sxs-lookup"><span data-stu-id="1693f-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="1693f-105">從 .NET Framework 4.8 開始，所使用的演算法是 SHA256。</span><span class="sxs-lookup"><span data-stu-id="1693f-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="1693f-106">為了與 WorkflowMarkupSourceAttribute.MD5Digest 相容，只會使用所產生總和檢查碼的前 16 個位元組。這可能會在偵錯時造成問題。</span><span class="sxs-lookup"><span data-stu-id="1693f-106">To be compatible with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="1693f-107">您可能需要重新建置您的專案。</span><span class="sxs-lookup"><span data-stu-id="1693f-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1693f-108">建議</span><span class="sxs-lookup"><span data-stu-id="1693f-108">Suggestion</span></span>

<span data-ttu-id="1693f-109">若重新建置您的專案沒有解決問題，請嘗試將 `AppContext` 切換 &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; 設為 True。在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="1693f-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="1693f-110">或是在組態檔內 (這需要在您所使用 MSBuild.exe 的 MSBuild.exe.config 中)：</span><span class="sxs-lookup"><span data-stu-id="1693f-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1693f-111">名稱</span><span class="sxs-lookup"><span data-stu-id="1693f-111">Name</span></span>    | <span data-ttu-id="1693f-112">值</span><span class="sxs-lookup"><span data-stu-id="1693f-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1693f-113">範圍</span><span class="sxs-lookup"><span data-stu-id="1693f-113">Scope</span></span>   | <span data-ttu-id="1693f-114">Minor</span><span class="sxs-lookup"><span data-stu-id="1693f-114">Minor</span></span>       |
| <span data-ttu-id="1693f-115">版本</span><span class="sxs-lookup"><span data-stu-id="1693f-115">Version</span></span> | <span data-ttu-id="1693f-116">4.8</span><span class="sxs-lookup"><span data-stu-id="1693f-116">4.8</span></span>         |
| <span data-ttu-id="1693f-117">類型</span><span class="sxs-lookup"><span data-stu-id="1693f-117">Type</span></span>    | <span data-ttu-id="1693f-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="1693f-118">Retargeting</span></span> |

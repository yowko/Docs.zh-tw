---
ms.openlocfilehash: f007a2b81820a1d25a2d101b35f3a49e7794fec1
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859088"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a><span data-ttu-id="ea39d-101">工作流程總和檢查碼從 MD5 變更為 SHA1</span><span class="sxs-lookup"><span data-stu-id="ea39d-101">Workflow checksums changed from MD5 to SHA1</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ea39d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ea39d-102">Details</span></span>|<span data-ttu-id="ea39d-103">為了支援使用 Visual Studio 進行偵錯，工作流程執行階段會使用雜湊演算法為工作流程執行個體產生總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="ea39d-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow instance using a hashing algorithm.</span></span> <span data-ttu-id="ea39d-104">在 .NET Framework 4.6.2 和更早版本中，工作流程總和檢查碼雜湊使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。</span><span class="sxs-lookup"><span data-stu-id="ea39d-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="ea39d-105">從 .NET Framework 4.7 開始，演算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="ea39d-105">Starting with the .NET Framework 4.7, the algorithm is SHA1.</span></span> <span data-ttu-id="ea39d-106">如果您的程式碼已保存這些總和檢查碼，就會不相容。</span><span class="sxs-lookup"><span data-stu-id="ea39d-106">If your code has persisted these checksums, they will be incompatible.</span></span>|
|<span data-ttu-id="ea39d-107">建議</span><span class="sxs-lookup"><span data-stu-id="ea39d-107">Suggestion</span></span>|<span data-ttu-id="ea39d-108">如果您的程式碼因為總和檢查碼失敗而無法載入工作流程執行個體，請嘗試將 <code>AppContext</code> 參數 &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; 設為 true。在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="ea39d-108">If your code is unable to load workflow instances due to a checksum failure, try setting the <code>AppContext</code> switch &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; to true.In code:</span></span><pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre><span data-ttu-id="ea39d-109">或者，在組態中：</span><span class="sxs-lookup"><span data-stu-id="ea39d-109">Or in configuration:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="ea39d-110">範圍</span><span class="sxs-lookup"><span data-stu-id="ea39d-110">Scope</span></span>|<span data-ttu-id="ea39d-111">次要</span><span class="sxs-lookup"><span data-stu-id="ea39d-111">Minor</span></span>|
|<span data-ttu-id="ea39d-112">版本</span><span class="sxs-lookup"><span data-stu-id="ea39d-112">Version</span></span>|<span data-ttu-id="ea39d-113">4.7</span><span class="sxs-lookup"><span data-stu-id="ea39d-113">4.7</span></span>|
|<span data-ttu-id="ea39d-114">類型</span><span class="sxs-lookup"><span data-stu-id="ea39d-114">Type</span></span>|<span data-ttu-id="ea39d-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="ea39d-115">Retargeting</span></span>|


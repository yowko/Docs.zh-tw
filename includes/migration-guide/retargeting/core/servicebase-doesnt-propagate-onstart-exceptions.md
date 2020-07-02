---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614369"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a><span data-ttu-id="f0b21-101">ServiceBase 不會傳播 OnStart 例外狀況</span><span class="sxs-lookup"><span data-stu-id="f0b21-101">ServiceBase doesn't propagate OnStart exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="f0b21-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0b21-102">Details</span></span>

<span data-ttu-id="f0b21-103">在 .NET Framework 4.7 和更早版本中，在服務啟動時擲回的例外狀況不會傳播至 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> 的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="f0b21-103">In the .NET Framework 4.7 and earlier versions, exceptions thrown on service startup are not propagated to the caller of <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span></span><br/><span data-ttu-id="f0b21-104">從 .NET Framework 4.7.1 為目標的應用程式開始，執行階段會為無法啟動的服務將例外狀況傳播到 <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f0b21-104">Starting with applications that target the .NET Framework 4.7.1, the runtime propagates exceptions to <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> for services that fail to start.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f0b21-105">建議</span><span class="sxs-lookup"><span data-stu-id="f0b21-105">Suggestion</span></span>

<span data-ttu-id="f0b21-106">在服務啟動時，如果有例外狀況，將會傳播該例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0b21-106">On service start, if there is an exception, that exception will be propagated.</span></span> <span data-ttu-id="f0b21-107">這應該有利於診斷服務無法啟動的情況。</span><span class="sxs-lookup"><span data-stu-id="f0b21-107">This should help diagnose cases where services fail to start.</span></span> <br/><span data-ttu-id="f0b21-108">如果不需要此行為，您可以在應用程式組態檔的 &lt;runtime&gt; 區段中新增以下 &lt;AppContextSwitchOverrides&gt; 元素，以選擇退出：</span><span class="sxs-lookup"><span data-stu-id="f0b21-108">If this behavior is undesirable, you can opt out of it by adding the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

<span data-ttu-id="f0b21-109">如果您的應用程式以比 4.7.1 舊的版本為目標，但您想要有這種行為，請在應用程式設定檔的 &lt;runtime&gt; 區段中新增以下 &lt;AppContextSwitchOverrides&gt; 元素：</span><span class="sxs-lookup"><span data-stu-id="f0b21-109">If your application targets an earlier version than 4.7.1 but you want to have this behavior, add the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| <span data-ttu-id="f0b21-110">名稱</span><span class="sxs-lookup"><span data-stu-id="f0b21-110">Name</span></span>    | <span data-ttu-id="f0b21-111">值</span><span class="sxs-lookup"><span data-stu-id="f0b21-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f0b21-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="f0b21-112">Scope</span></span>   | <span data-ttu-id="f0b21-113">Minor</span><span class="sxs-lookup"><span data-stu-id="f0b21-113">Minor</span></span>       |
| <span data-ttu-id="f0b21-114">版本</span><span class="sxs-lookup"><span data-stu-id="f0b21-114">Version</span></span> | <span data-ttu-id="f0b21-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="f0b21-115">4.7.1</span></span>       |
| <span data-ttu-id="f0b21-116">類型</span><span class="sxs-lookup"><span data-stu-id="f0b21-116">Type</span></span>    | <span data-ttu-id="f0b21-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="f0b21-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f0b21-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f0b21-118">Affected APIs</span></span>

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>

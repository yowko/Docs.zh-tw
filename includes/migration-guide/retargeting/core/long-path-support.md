---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614348"
---
### <a name="long-path-support"></a><span data-ttu-id="33b99-101">長路徑支援</span><span class="sxs-lookup"><span data-stu-id="33b99-101">Long path support</span></span>

#### <a name="details"></a><span data-ttu-id="33b99-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="33b99-102">Details</span></span>

<span data-ttu-id="33b99-103">從以 .NET Framework 4.6.2 為目標的應用程式開始，支援長路徑 (最多 32K 個字元)，且已移除對於路徑長度的 260 個字元 (或 `MAX_PATH`) 限制。若為重新編譯以 .NET Framework 4.6.2 為目標的應用程式，先前因為路徑超過 260 個字元而擲回 <xref:System.IO.PathTooLongException?displayProperty=fullName> 的程式碼路徑，現在將只有在下列情況下擲回 <xref:System.IO.PathTooLongException?displayProperty=fullName>：</span><span class="sxs-lookup"><span data-stu-id="33b99-103">Starting with apps that target the .NET Framework 4.6.2, long paths (of up to 32K characters) are supported, and the 260-character (or `MAX_PATH`) limitation on path lengths has been removed.For apps that are recompiled to target the .NET Framework 4.6.2, code paths that previously threw a <xref:System.IO.PathTooLongException?displayProperty=fullName> because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException?displayProperty=fullName> only under the following conditions:</span></span>

- <span data-ttu-id="33b99-104">路徑的長度大於 <xref:System.Int16.MaxValue> (32,767) 個字元。</span><span class="sxs-lookup"><span data-stu-id="33b99-104">The length of the path is greater than <xref:System.Int16.MaxValue> (32,767) characters.</span></span>
- <span data-ttu-id="33b99-105">作業系統傳回 `COR_E_PATHTOOLONG` 或其對應項。</span><span class="sxs-lookup"><span data-stu-id="33b99-105">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>
<span data-ttu-id="33b99-106">若為以 .NET Framework 4.6.1 和更早版本為目標的應用程式，每當路徑超過 260 個字元時，執行階段就會自動擲回 <xref:System.IO.PathTooLongException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="33b99-106">For apps that target the .NET Framework 4.6.1 and earlier versions, the runtime automatically throws a <xref:System.IO.PathTooLongException?displayProperty=fullName> whenever a path exceeds 260 characters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="33b99-107">建議</span><span class="sxs-lookup"><span data-stu-id="33b99-107">Suggestion</span></span>

<span data-ttu-id="33b99-108">若為以 .NET Framework 4.6.2 為目標的應用程式，如果不需要長路徑支援，您可以透過將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段以選擇退出長路徑支援︰</span><span class="sxs-lookup"><span data-stu-id="33b99-108">For apps that target the .NET Framework 4.6.2, you can opt out of long path support if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

<span data-ttu-id="33b99-109">若為以舊版 .NET Framework 為目標但卻在 .NET Framework 4.6.2 或更新版本上執行的應用程式，則可將下列內容新增至 `app.config` 檔案的 `<runtime>` 區段，以選擇加入長路徑支援：</span><span class="sxs-lookup"><span data-stu-id="33b99-109">For apps that target earlier versions of the .NET Framework but run on the .NET Framework 4.6.2 or later, you can opt in to long path support by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| <span data-ttu-id="33b99-110">名稱</span><span class="sxs-lookup"><span data-stu-id="33b99-110">Name</span></span>    | <span data-ttu-id="33b99-111">值</span><span class="sxs-lookup"><span data-stu-id="33b99-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="33b99-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="33b99-112">Scope</span></span>   | <span data-ttu-id="33b99-113">Minor</span><span class="sxs-lookup"><span data-stu-id="33b99-113">Minor</span></span>       |
| <span data-ttu-id="33b99-114">版本</span><span class="sxs-lookup"><span data-stu-id="33b99-114">Version</span></span> | <span data-ttu-id="33b99-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="33b99-115">4.6.2</span></span>       |
| <span data-ttu-id="33b99-116">類型</span><span class="sxs-lookup"><span data-stu-id="33b99-116">Type</span></span>    | <span data-ttu-id="33b99-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="33b99-117">Retargeting</span></span> |

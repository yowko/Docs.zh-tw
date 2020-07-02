---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617794"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="8d997-101">符號的工作流程 XAML 總和檢查碼從 SHA1 變更為 SHA256</span><span class="sxs-lookup"><span data-stu-id="8d997-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="8d997-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8d997-102">Details</span></span>

<span data-ttu-id="8d997-103">為了支援 Visual Studio 偵錯，工作流程執行階段會使用雜湊演算法為工作流程 XAML 檔案產生總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="8d997-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="8d997-104">在 .NET Framework 4.6.2 和更早版本中，工作流程總和檢查碼雜湊使用 MD5 演算法，它會在啟用 FIPS 的系統上造成問題。</span><span class="sxs-lookup"><span data-stu-id="8d997-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="8d997-105">從 .NET Framework 4.7 開始，預設的演算法已變更為 SHA1。</span><span class="sxs-lookup"><span data-stu-id="8d997-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="8d997-106">從 .NET Framework 4.8 開始，預設的演算法已變更為 SHA256。</span><span class="sxs-lookup"><span data-stu-id="8d997-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8d997-107">建議</span><span class="sxs-lookup"><span data-stu-id="8d997-107">Suggestion</span></span>

<span data-ttu-id="8d997-108">如果您的程式碼因為總和檢查碼失敗而無法載入工作流程實例或尋找適當的符號，請嘗試將參數設定為「 `AppContext` Switch.System。UseSHA1HashForDebuggerSymbols "to `true` 。</span><span class="sxs-lookup"><span data-stu-id="8d997-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the `AppContext` switch "Switch.System.Activities.UseSHA1HashForDebuggerSymbols" to `true`.</span></span> <span data-ttu-id="8d997-109">在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="8d997-109">In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

<span data-ttu-id="8d997-110">或者，在組態中：</span><span class="sxs-lookup"><span data-stu-id="8d997-110">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="8d997-111">名稱</span><span class="sxs-lookup"><span data-stu-id="8d997-111">Name</span></span>    | <span data-ttu-id="8d997-112">值</span><span class="sxs-lookup"><span data-stu-id="8d997-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8d997-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8d997-113">Scope</span></span>   | <span data-ttu-id="8d997-114">Minor</span><span class="sxs-lookup"><span data-stu-id="8d997-114">Minor</span></span>       |
| <span data-ttu-id="8d997-115">版本</span><span class="sxs-lookup"><span data-stu-id="8d997-115">Version</span></span> | <span data-ttu-id="8d997-116">4.8</span><span class="sxs-lookup"><span data-stu-id="8d997-116">4.8</span></span>         |
| <span data-ttu-id="8d997-117">類型</span><span class="sxs-lookup"><span data-stu-id="8d997-117">Type</span></span>    | <span data-ttu-id="8d997-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8d997-118">Retargeting</span></span> |

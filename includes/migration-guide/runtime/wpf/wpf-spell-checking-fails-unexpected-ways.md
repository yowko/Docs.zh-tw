---
ms.openlocfilehash: d4e60f2a59980263916718ebcc71cc359952c031
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497312"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="1b653-101">WPF 拼字檢查以非預期的方式失敗</span><span class="sxs-lookup"><span data-stu-id="1b653-101">WPF Spell Checking fails in unexpected ways</span></span>

#### <a name="details"></a><span data-ttu-id="1b653-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1b653-102">Details</span></span>

<span data-ttu-id="1b653-103">這包括一些 WPF 拼字檢查工具問題：</span><span class="sxs-lookup"><span data-stu-id="1b653-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="1b653-104">WPF 拼字檢查工具有時會擲回 <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1b653-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=fullName></span></span></li><li><span data-ttu-id="1b653-105">使用 [以不同的使用者身分執行] 來啟動應用程式時，WPF 拼字檢查工具會失敗並顯示 <xref:System.UnauthorizedAccessException></span><span class="sxs-lookup"><span data-stu-id="1b653-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="1b653-106">WPF 拼字檢查工具會誤將複合字識別為拼字錯誤，例如德文中的 'Hausnummer'。</span><span class="sxs-lookup"><span data-stu-id="1b653-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="1b653-107">建議</span><span class="sxs-lookup"><span data-stu-id="1b653-107">Suggestion</span></span>

<span data-ttu-id="1b653-108">問題 #1 - 此問題已在 .NET Framework 4.6.2 中修正。問題 #2 - 使用 [以不同的使用者身分執行] 來啟動應用程式時，不再支援 WPF 拼字檢查工具。</span><span class="sxs-lookup"><span data-stu-id="1b653-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="1b653-109">從 .NET Framework 4.6.2 開始，以這種方式啟動的應用程式將不會再意外損毀 - 而是以無訊息的方式停用拼字檢查工具。</span><span class="sxs-lookup"><span data-stu-id="1b653-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="1b653-110">問題 #3 - 此問題已在 .NET Framework 4.6.2 中修正。</span><span class="sxs-lookup"><span data-stu-id="1b653-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="1b653-111">名稱</span><span class="sxs-lookup"><span data-stu-id="1b653-111">Name</span></span>    | <span data-ttu-id="1b653-112">值</span><span class="sxs-lookup"><span data-stu-id="1b653-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1b653-113">範圍</span><span class="sxs-lookup"><span data-stu-id="1b653-113">Scope</span></span>   |<span data-ttu-id="1b653-114">Edge</span><span class="sxs-lookup"><span data-stu-id="1b653-114">Edge</span></span>|
|<span data-ttu-id="1b653-115">版本</span><span class="sxs-lookup"><span data-stu-id="1b653-115">Version</span></span>|<span data-ttu-id="1b653-116">4.6.1</span><span class="sxs-lookup"><span data-stu-id="1b653-116">4.6.1</span></span>|
|<span data-ttu-id="1b653-117">類型</span><span class="sxs-lookup"><span data-stu-id="1b653-117">Type</span></span>|<span data-ttu-id="1b653-118">執行階段</span><span class="sxs-lookup"><span data-stu-id="1b653-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1b653-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1b653-119">Affected APIs</span></span>

<span data-ttu-id="1b653-120">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="1b653-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

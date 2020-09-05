---
ms.openlocfilehash: 3244913e06a744dafc4440f824ebe6bed25b8dd1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497444"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="735f9-101">WPF 拼字檢查功能所擲回的 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="735f9-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="735f9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="735f9-102">Details</span></span>

<span data-ttu-id="735f9-103">在應用程式關閉期間，WPF 應用程式偶爾會因拼字檢查功能所擲回的 <xref:System.ObjectDisposedException?displayProperty=fullName> 而損毀。</span><span class="sxs-lookup"><span data-stu-id="735f9-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="735f9-104">此問題已在 .NET Framework 4.7 WPF 中透過依正常程序處理例外狀況來修正，進而確保應用程式不會再受到負面影響。</span><span class="sxs-lookup"><span data-stu-id="735f9-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="735f9-105">請注意，在偵錯工具下執行的應用程式偶爾還是會發生第一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="735f9-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="735f9-106">建議</span><span class="sxs-lookup"><span data-stu-id="735f9-106">Suggestion</span></span>

<span data-ttu-id="735f9-107">升級至 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="735f9-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="735f9-108">名稱</span><span class="sxs-lookup"><span data-stu-id="735f9-108">Name</span></span>    | <span data-ttu-id="735f9-109">值</span><span class="sxs-lookup"><span data-stu-id="735f9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="735f9-110">範圍</span><span class="sxs-lookup"><span data-stu-id="735f9-110">Scope</span></span>   |<span data-ttu-id="735f9-111">Edge</span><span class="sxs-lookup"><span data-stu-id="735f9-111">Edge</span></span>|
|<span data-ttu-id="735f9-112">版本</span><span class="sxs-lookup"><span data-stu-id="735f9-112">Version</span></span>|<span data-ttu-id="735f9-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="735f9-113">4.6.1</span></span>|
|<span data-ttu-id="735f9-114">類型</span><span class="sxs-lookup"><span data-stu-id="735f9-114">Type</span></span>|<span data-ttu-id="735f9-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="735f9-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="735f9-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="735f9-116">Affected APIs</span></span>

<span data-ttu-id="735f9-117">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="735f9-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

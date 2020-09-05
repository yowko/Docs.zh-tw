---
ms.openlocfilehash: 1487b5f47966cfcae0e47848dae99b39b42db18d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496234"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="4610e-101">已改進 WPF 中的按鍵提示行為</span><span class="sxs-lookup"><span data-stu-id="4610e-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="4610e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4610e-102">Details</span></span>

<span data-ttu-id="4610e-103">按鍵提示行為已經過修改，讓 Microsoft Word 與 Windows 檔案總管之間的行為趨於一致。</span><span class="sxs-lookup"><span data-stu-id="4610e-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="4610e-104">WPF 會藉由查看是否已啟用按鍵提示狀態，或是並非按下 <xref:System.Windows.Input.KeyEventArgs.SystemKey> (特別是 <xref:System.Windows.Input.Key> 或 <xref:System.Windows.Input.Key.F11>) 的情況，正確地處理按鍵提示的按鍵。</span><span class="sxs-lookup"><span data-stu-id="4610e-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="4610e-105">現在即使滑鼠已開啟了按鍵提示，其仍會關閉功能表。</span><span class="sxs-lookup"><span data-stu-id="4610e-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4610e-106">建議</span><span class="sxs-lookup"><span data-stu-id="4610e-106">Suggestion</span></span>

<span data-ttu-id="4610e-107">N/A</span><span class="sxs-lookup"><span data-stu-id="4610e-107">N/A</span></span>

| <span data-ttu-id="4610e-108">名稱</span><span class="sxs-lookup"><span data-stu-id="4610e-108">Name</span></span>    | <span data-ttu-id="4610e-109">值</span><span class="sxs-lookup"><span data-stu-id="4610e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4610e-110">範圍</span><span class="sxs-lookup"><span data-stu-id="4610e-110">Scope</span></span>   |<span data-ttu-id="4610e-111">Edge</span><span class="sxs-lookup"><span data-stu-id="4610e-111">Edge</span></span>|
|<span data-ttu-id="4610e-112">版本</span><span class="sxs-lookup"><span data-stu-id="4610e-112">Version</span></span>|<span data-ttu-id="4610e-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="4610e-113">4.7.2</span></span>|
|<span data-ttu-id="4610e-114">類型</span><span class="sxs-lookup"><span data-stu-id="4610e-114">Type</span></span>|<span data-ttu-id="4610e-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="4610e-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4610e-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4610e-116">Affected APIs</span></span>

<span data-ttu-id="4610e-117">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="4610e-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

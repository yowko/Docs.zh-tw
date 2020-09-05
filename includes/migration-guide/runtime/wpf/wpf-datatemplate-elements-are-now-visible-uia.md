---
ms.openlocfilehash: 4394e69dafeb6cce2d7719a67bbce396d3bc1086
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497116"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="4afea-101">UIA 現在看得到 WPF DataTemplate 項目</span><span class="sxs-lookup"><span data-stu-id="4afea-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="4afea-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4afea-102">Details</span></span>

<span data-ttu-id="4afea-103">之前，UI 自動化看不到 <xref:System.Windows.DataTemplate?displayProperty=fullName> 項目。</span><span class="sxs-lookup"><span data-stu-id="4afea-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="4afea-104">從 4.5 開始，使用者介面自動化將會偵測這些項目。</span><span class="sxs-lookup"><span data-stu-id="4afea-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="4afea-105">這在許多情況下很有用，但可能會中斷相依於不含 <xref:System.Windows.DataTemplate?displayProperty=fullName> 項目之 UIA 樹狀目錄的測試。</span><span class="sxs-lookup"><span data-stu-id="4afea-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4afea-106">建議</span><span class="sxs-lookup"><span data-stu-id="4afea-106">Suggestion</span></span>

<span data-ttu-id="4afea-107">您可能需要更新此應用程式的 UI 自動化測試，UIA 樹狀目錄現在才能包含先前不可見的 <xref:System.Windows.DataTemplate?displayProperty=fullName> 項目。</span><span class="sxs-lookup"><span data-stu-id="4afea-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="4afea-108">例如，預期某些項目彼此相鄰的測試，現在可能需要預期這些項目之間會出現先前不可見的 UIA 項目。</span><span class="sxs-lookup"><span data-stu-id="4afea-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="4afea-109">或者，依賴幾個 UIA 項目或其索引的測試，可能需要以新值更新。</span><span class="sxs-lookup"><span data-stu-id="4afea-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="4afea-110">名稱</span><span class="sxs-lookup"><span data-stu-id="4afea-110">Name</span></span>    | <span data-ttu-id="4afea-111">值</span><span class="sxs-lookup"><span data-stu-id="4afea-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4afea-112">範圍</span><span class="sxs-lookup"><span data-stu-id="4afea-112">Scope</span></span>   |<span data-ttu-id="4afea-113">Edge</span><span class="sxs-lookup"><span data-stu-id="4afea-113">Edge</span></span>|
|<span data-ttu-id="4afea-114">版本</span><span class="sxs-lookup"><span data-stu-id="4afea-114">Version</span></span>|<span data-ttu-id="4afea-115">4.5</span><span class="sxs-lookup"><span data-stu-id="4afea-115">4.5</span></span>|
|<span data-ttu-id="4afea-116">類型</span><span class="sxs-lookup"><span data-stu-id="4afea-116">Type</span></span>|<span data-ttu-id="4afea-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="4afea-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4afea-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4afea-118">Affected APIs</span></span>

- <xref:System.Windows.DataTemplate.%23ctor>
- <xref:System.Windows.DataTemplate.%23ctor(System.Object)>

<!--

#### Affected APIs

- `M:System.Windows.DataTemplate.#ctor`
- `M:System.Windows.DataTemplate.#ctor(System.Object)`

-->

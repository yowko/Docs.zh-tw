---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616039"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a><span data-ttu-id="396e5-101">不支援具有非公用 setter 之屬性的雙向資料繫結</span><span class="sxs-lookup"><span data-stu-id="396e5-101">Two-way data-binding to a property with a non-public setter is not supported</span></span>

#### <a name="details"></a><span data-ttu-id="396e5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="396e5-102">Details</span></span>

<span data-ttu-id="396e5-103">嘗試將資料繫結至不含公用 setter 的屬性，是之前從未支援過的情況。</span><span class="sxs-lookup"><span data-stu-id="396e5-103">Attempting to data bind to a property without a public setter has never been a supported scenario.</span></span> <span data-ttu-id="396e5-104">從 .NET Framework 4.5.1 開始，這種情況將會擲回 <xref:System.InvalidOperationException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="396e5-104">Beginning in the .NET Framework 4.5.1, this scenario will throw an <xref:System.InvalidOperationException?displayProperty=fullName>.</span></span> <span data-ttu-id="396e5-105">請注意，只有專門以 .NET Framework 4.5.1 為目標的應用程式才會擲回此新的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="396e5-105">Note that this new exception will only be thrown for apps that specifically target the .NET Framework 4.5.1.</span></span> <span data-ttu-id="396e5-106">如果應用程式是以 .NET Framework 4.5 為目標，則會允許此呼叫。</span><span class="sxs-lookup"><span data-stu-id="396e5-106">If an app targets the .NET Framework 4.5, the call will be allowed.</span></span> <span data-ttu-id="396e5-107">如果應用程式未以特定 .NET Framework 版本為目標，則會將繫結視為單向。</span><span class="sxs-lookup"><span data-stu-id="396e5-107">If the app does not target a particular .NET Framework version, the binding will be treated as one-way.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="396e5-108">建議</span><span class="sxs-lookup"><span data-stu-id="396e5-108">Suggestion</span></span>

<span data-ttu-id="396e5-109">您應該更新應用程式以使用單向繫結，或以公用方式公開屬性的 setter。</span><span class="sxs-lookup"><span data-stu-id="396e5-109">The app should be updated to either use one-way binding, or expose the property's setter publicly.</span></span> <span data-ttu-id="396e5-110">此外，以 .NET Framework 4.5 為目標也會使應用程式展示舊版行為。</span><span class="sxs-lookup"><span data-stu-id="396e5-110">Alternatively, targeting the .NET Framework 4.5 will cause the app to exhibit the old behavior.</span></span>

| <span data-ttu-id="396e5-111">名稱</span><span class="sxs-lookup"><span data-stu-id="396e5-111">Name</span></span>    | <span data-ttu-id="396e5-112">值</span><span class="sxs-lookup"><span data-stu-id="396e5-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="396e5-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="396e5-113">Scope</span></span>   | <span data-ttu-id="396e5-114">Minor</span><span class="sxs-lookup"><span data-stu-id="396e5-114">Minor</span></span>       |
| <span data-ttu-id="396e5-115">版本</span><span class="sxs-lookup"><span data-stu-id="396e5-115">Version</span></span> | <span data-ttu-id="396e5-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="396e5-116">4.5.1</span></span>       |
| <span data-ttu-id="396e5-117">類型</span><span class="sxs-lookup"><span data-stu-id="396e5-117">Type</span></span>    | <span data-ttu-id="396e5-118">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="396e5-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="396e5-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="396e5-119">Affected APIs</span></span>

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>

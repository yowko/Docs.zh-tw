---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617145"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="b04c4-101">XML 結構描述驗證更嚴格</span><span class="sxs-lookup"><span data-stu-id="b04c4-101">XML schema validation is stricter</span></span>

#### <a name="details"></a><span data-ttu-id="b04c4-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b04c4-102">Details</span></span>

<span data-ttu-id="b04c4-103">在 .NET Framework 4.5 中，XML 結構描述驗證更為嚴格。</span><span class="sxs-lookup"><span data-stu-id="b04c4-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="b04c4-104">如果您使用 xsd:anyURI 驗證 URI (例如 mailto 通訊協定)，而 URI 中有空格，則驗證會失敗。</span><span class="sxs-lookup"><span data-stu-id="b04c4-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="b04c4-105">在舊版 .NET Framework 中，驗證會成功。</span><span class="sxs-lookup"><span data-stu-id="b04c4-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="b04c4-106">這項變更只會影響以 .NET Framework 4.5 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b04c4-106">The change affects only applications that target the .NET Framework 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b04c4-107">建議</span><span class="sxs-lookup"><span data-stu-id="b04c4-107">Suggestion</span></span>

<span data-ttu-id="b04c4-108">如果需要較鬆散的 .NET Framework 4.0 驗證，正在驗證的應用程式可以將目標設為 .NET Framework 4.0 版。</span><span class="sxs-lookup"><span data-stu-id="b04c4-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="b04c4-109">不過，將目標重定為 .NET Framework 4.5 時，應該完成程式碼檢閱，以確定無效的 URI (含空格) 不會作為 anyURI 資料類型的屬性值。</span><span class="sxs-lookup"><span data-stu-id="b04c4-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>

| <span data-ttu-id="b04c4-110">名稱</span><span class="sxs-lookup"><span data-stu-id="b04c4-110">Name</span></span>    | <span data-ttu-id="b04c4-111">值</span><span class="sxs-lookup"><span data-stu-id="b04c4-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b04c4-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="b04c4-112">Scope</span></span>   | <span data-ttu-id="b04c4-113">Minor</span><span class="sxs-lookup"><span data-stu-id="b04c4-113">Minor</span></span>       |
| <span data-ttu-id="b04c4-114">版本</span><span class="sxs-lookup"><span data-stu-id="b04c4-114">Version</span></span> | <span data-ttu-id="b04c4-115">4.5</span><span class="sxs-lookup"><span data-stu-id="b04c4-115">4.5</span></span>         |
| <span data-ttu-id="b04c4-116">類型</span><span class="sxs-lookup"><span data-stu-id="b04c4-116">Type</span></span>    | <span data-ttu-id="b04c4-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="b04c4-117">Retargeting</span></span> |

---
ms.openlocfilehash: 6431f3b4d0983c44629e4fe760c75adcc277ddd4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496685"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="aa79e-101">某些 .NET API 會造成第一個可能發生 (已處理) 的 EntryPointNotFoundException</span><span class="sxs-lookup"><span data-stu-id="aa79e-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="aa79e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aa79e-102">Details</span></span>

<span data-ttu-id="aa79e-103">在 .NET Framework 4.5 中，少數 .NET 方法已開始擲回第一個可能發生的 <xref:System.EntryPointNotFoundException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="aa79e-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="aa79e-104">這些例外狀況在 .NET Framework 中已處理，但可能會中斷未預期第一個可能發生例外狀況的測試自動化。</span><span class="sxs-lookup"><span data-stu-id="aa79e-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="aa79e-105">這些相同的 API 會在啟用 HighVersionLie 時中斷一些 ApiVerifier 案例。</span><span class="sxs-lookup"><span data-stu-id="aa79e-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="aa79e-106">建議</span><span class="sxs-lookup"><span data-stu-id="aa79e-106">Suggestion</span></span>

<span data-ttu-id="aa79e-107">您可以升級至 .NET Framework 4.5.1 來避免此錯誤 (bug)。</span><span class="sxs-lookup"><span data-stu-id="aa79e-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="aa79e-108">或者，您也可以更新測試自動化，不要在發生第一個可能的 <xref:System.EntryPointNotFoundException?displayProperty=fullName> 時中斷。</span><span class="sxs-lookup"><span data-stu-id="aa79e-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="aa79e-109">名稱</span><span class="sxs-lookup"><span data-stu-id="aa79e-109">Name</span></span>    | <span data-ttu-id="aa79e-110">值</span><span class="sxs-lookup"><span data-stu-id="aa79e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aa79e-111">範圍</span><span class="sxs-lookup"><span data-stu-id="aa79e-111">Scope</span></span>   |<span data-ttu-id="aa79e-112">Edge</span><span class="sxs-lookup"><span data-stu-id="aa79e-112">Edge</span></span>|
|<span data-ttu-id="aa79e-113">版本</span><span class="sxs-lookup"><span data-stu-id="aa79e-113">Version</span></span>|<span data-ttu-id="aa79e-114">4.5</span><span class="sxs-lookup"><span data-stu-id="aa79e-114">4.5</span></span>|
|<span data-ttu-id="aa79e-115">類型</span><span class="sxs-lookup"><span data-stu-id="aa79e-115">Type</span></span>|<span data-ttu-id="aa79e-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="aa79e-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aa79e-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="aa79e-117">Affected APIs</span></span>

- <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)>

<!--

#### Affected APIs

- `M:System.Diagnostics.Debug.Assert(System.Boolean)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)`
- `M:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])`
- `M:System.Xml.Serialization.XmlSerializer.#ctor(System.Type)`

-->

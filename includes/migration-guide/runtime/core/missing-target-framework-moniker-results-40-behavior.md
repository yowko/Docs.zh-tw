---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619983"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a><span data-ttu-id="eaf90-101">在 4.0 行為中遺漏目標 Framework Moniker 結果</span><span class="sxs-lookup"><span data-stu-id="eaf90-101">Missing Target Framework Moniker results in 4.0 behavior</span></span>

#### <a name="details"></a><span data-ttu-id="eaf90-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="eaf90-102">Details</span></span>

<span data-ttu-id="eaf90-103">未在組件層級套用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 的應用程式將會使用 .NET Framework 4.0 的語意 (Quirks) 來自動執行。</span><span class="sxs-lookup"><span data-stu-id="eaf90-103">Applications without a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> applied at the assembly level will automatically run using the semantics (quirks) of the .NET Framework 4.0.</span></span> <span data-ttu-id="eaf90-104">為了確保有高品質，建議明確設定所有二進位檔的 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 屬性，以指出用來建置的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="eaf90-104">To ensure high quality, it is recommended that all binaries be explicitly attributed with a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> indicating the version of the .NET Framework they were built with.</span></span> <span data-ttu-id="eaf90-105">請注意，在專案檔中使用目標 Framework Moniker 會使 MSBuild 自動套用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="eaf90-105">Note that using a target framework moniker in a project file will cause MSBuild to automatically apply a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eaf90-106">建議</span><span class="sxs-lookup"><span data-stu-id="eaf90-106">Suggestion</span></span>

<span data-ttu-id="eaf90-107">您應該透過直接將屬性新增至組件，或藉由[在專案檔中或透過 Visual Studio 的專案屬性 GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/) 來指定目標 Framework，以提供 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="eaf90-107">A <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> should be supplied, either through adding the attribute directly to the assembly or by specifying a target framework in the [project file or through Visual Studio's project properties GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/).</span></span>

| <span data-ttu-id="eaf90-108">名稱</span><span class="sxs-lookup"><span data-stu-id="eaf90-108">Name</span></span>    | <span data-ttu-id="eaf90-109">值</span><span class="sxs-lookup"><span data-stu-id="eaf90-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eaf90-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="eaf90-110">Scope</span></span>   |<span data-ttu-id="eaf90-111">主要</span><span class="sxs-lookup"><span data-stu-id="eaf90-111">Major</span></span>|
|<span data-ttu-id="eaf90-112">版本</span><span class="sxs-lookup"><span data-stu-id="eaf90-112">Version</span></span>|<span data-ttu-id="eaf90-113">4.5</span><span class="sxs-lookup"><span data-stu-id="eaf90-113">4.5</span></span>|
|<span data-ttu-id="eaf90-114">類型</span><span class="sxs-lookup"><span data-stu-id="eaf90-114">Type</span></span>|<span data-ttu-id="eaf90-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="eaf90-115">Runtime</span></span>|

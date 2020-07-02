---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616038"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a><span data-ttu-id="d1f7d-101">ObsoleteAttribute 會在 WinMD 案例中匯出為 ObsoleteAttribute 和 DeprecatedAttribute</span><span class="sxs-lookup"><span data-stu-id="d1f7d-101">ObsoleteAttribute exports as both ObsoleteAttribute and DeprecatedAttribute in WinMD scenarios</span></span>

#### <a name="details"></a><span data-ttu-id="d1f7d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1f7d-102">Details</span></span>

<span data-ttu-id="d1f7d-103">當您建立 Windows 中繼資料庫 (.winmd 檔案) 時，<xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性會匯出為 <xref:System.ObsoleteAttribute?displayProperty=fullName> 和 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)。</span><span class="sxs-lookup"><span data-stu-id="d1f7d-103">When you create a Windows Metadata library (.winmd file), the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute is exported as both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d1f7d-104">建議</span><span class="sxs-lookup"><span data-stu-id="d1f7d-104">Suggestion</span></span>

<span data-ttu-id="d1f7d-105">重新編譯使用 <xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性的現有來源程式碼，可能會在從 C++/CX 或 JavaScript 使用該程式碼時產生警告。我們不建議您在受控組件中同時套用 <xref:System.ObsoleteAttribute?displayProperty=fullName> 和 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)，這樣可能會導致建置警告。</span><span class="sxs-lookup"><span data-stu-id="d1f7d-105">Recompilation of existing source code that uses the <xref:System.ObsoleteAttribute?displayProperty=fullName> attribute may generate warnings when consuming that code from C++/CX or JavaScript.We do not recommend applying both <xref:System.ObsoleteAttribute?displayProperty=fullName> and [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute) to code in managed assemblies; it may result in build warnings.</span></span>

| <span data-ttu-id="d1f7d-106">名稱</span><span class="sxs-lookup"><span data-stu-id="d1f7d-106">Name</span></span>    | <span data-ttu-id="d1f7d-107">值</span><span class="sxs-lookup"><span data-stu-id="d1f7d-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d1f7d-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d1f7d-108">Scope</span></span>   | <span data-ttu-id="d1f7d-109">Edge</span><span class="sxs-lookup"><span data-stu-id="d1f7d-109">Edge</span></span>        |
| <span data-ttu-id="d1f7d-110">版本</span><span class="sxs-lookup"><span data-stu-id="d1f7d-110">Version</span></span> | <span data-ttu-id="d1f7d-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d1f7d-111">4.5.1</span></span>       |
| <span data-ttu-id="d1f7d-112">類型</span><span class="sxs-lookup"><span data-stu-id="d1f7d-112">Type</span></span>    | <span data-ttu-id="d1f7d-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="d1f7d-113">Retargeting</span></span> |

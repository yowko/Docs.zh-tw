---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619817"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="d78fc-101">HttpRequest.ContentEncoding 屬性禁止 UTF7</span><span class="sxs-lookup"><span data-stu-id="d78fc-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="d78fc-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d78fc-102">Details</span></span>

<span data-ttu-id="d78fc-103">從 .NET Framework 4.5 開始，在 <xref:System.Web.HttpRequest?displayProperty=fullName> 本文中禁止使用 UTF-7 編碼。</span><span class="sxs-lookup"><span data-stu-id="d78fc-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="d78fc-104">在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。</span><span class="sxs-lookup"><span data-stu-id="d78fc-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d78fc-105">建議</span><span class="sxs-lookup"><span data-stu-id="d78fc-105">Suggestion</span></span>

<span data-ttu-id="d78fc-106">在理想情況下，您應該更新應用程式，不要在 <xref:System.Web.HttpRequest?displayProperty=fullName> 中使用 UTF-7 編碼。</span><span class="sxs-lookup"><span data-stu-id="d78fc-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="d78fc-107">或者，您也可以使用 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 項目的 <code>aspnet:AllowUtf7RequestContentEncoding</code> 屬性還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="d78fc-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="d78fc-108">名稱</span><span class="sxs-lookup"><span data-stu-id="d78fc-108">Name</span></span>    | <span data-ttu-id="d78fc-109">值</span><span class="sxs-lookup"><span data-stu-id="d78fc-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d78fc-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d78fc-110">Scope</span></span>   |<span data-ttu-id="d78fc-111">Edge</span><span class="sxs-lookup"><span data-stu-id="d78fc-111">Edge</span></span>|
|<span data-ttu-id="d78fc-112">版本</span><span class="sxs-lookup"><span data-stu-id="d78fc-112">Version</span></span>|<span data-ttu-id="d78fc-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d78fc-113">4.5</span></span>|
|<span data-ttu-id="d78fc-114">類型</span><span class="sxs-lookup"><span data-stu-id="d78fc-114">Type</span></span>|<span data-ttu-id="d78fc-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="d78fc-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d78fc-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d78fc-116">Affected APIs</span></span>

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

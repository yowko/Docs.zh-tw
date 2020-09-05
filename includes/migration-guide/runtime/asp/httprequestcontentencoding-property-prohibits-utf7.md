---
ms.openlocfilehash: cf34c5df1badcfd86d8a07bafdf1b759234712e0
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497165"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="6dec3-101">HttpRequest.ContentEncoding 屬性禁止 UTF7</span><span class="sxs-lookup"><span data-stu-id="6dec3-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

#### <a name="details"></a><span data-ttu-id="6dec3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6dec3-102">Details</span></span>

<span data-ttu-id="6dec3-103">從 .NET Framework 4.5 開始，在 <xref:System.Web.HttpRequest?displayProperty=fullName> 本文中禁止使用 UTF-7 編碼。</span><span class="sxs-lookup"><span data-stu-id="6dec3-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=fullName>s' bodies.</span></span> <span data-ttu-id="6dec3-104">在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。</span><span class="sxs-lookup"><span data-stu-id="6dec3-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6dec3-105">建議</span><span class="sxs-lookup"><span data-stu-id="6dec3-105">Suggestion</span></span>

<span data-ttu-id="6dec3-106">在理想情況下，您應該更新應用程式，不要在 <xref:System.Web.HttpRequest?displayProperty=fullName> 中使用 UTF-7 編碼。</span><span class="sxs-lookup"><span data-stu-id="6dec3-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=fullName>s.</span></span> <span data-ttu-id="6dec3-107">或者，您也可以使用 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 項目的 <code>aspnet:AllowUtf7RequestContentEncoding</code> 屬性還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="6dec3-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>

| <span data-ttu-id="6dec3-108">名稱</span><span class="sxs-lookup"><span data-stu-id="6dec3-108">Name</span></span>    | <span data-ttu-id="6dec3-109">值</span><span class="sxs-lookup"><span data-stu-id="6dec3-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6dec3-110">範圍</span><span class="sxs-lookup"><span data-stu-id="6dec3-110">Scope</span></span>   |<span data-ttu-id="6dec3-111">Edge</span><span class="sxs-lookup"><span data-stu-id="6dec3-111">Edge</span></span>|
|<span data-ttu-id="6dec3-112">版本</span><span class="sxs-lookup"><span data-stu-id="6dec3-112">Version</span></span>|<span data-ttu-id="6dec3-113">4.5</span><span class="sxs-lookup"><span data-stu-id="6dec3-113">4.5</span></span>|
|<span data-ttu-id="6dec3-114">類型</span><span class="sxs-lookup"><span data-stu-id="6dec3-114">Type</span></span>|<span data-ttu-id="6dec3-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="6dec3-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6dec3-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6dec3-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.ContentEncoding`

-->

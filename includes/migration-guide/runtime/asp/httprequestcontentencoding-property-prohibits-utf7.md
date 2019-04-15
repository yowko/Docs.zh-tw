---
ms.openlocfilehash: 668d047d3247d64cb1400d4a9ea6887795fa0d44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235122"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a><span data-ttu-id="5a4a2-101">HttpRequest.ContentEncoding 屬性禁止 UTF7</span><span class="sxs-lookup"><span data-stu-id="5a4a2-101">HttpRequest.ContentEncoding property prohibits UTF7</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5a4a2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5a4a2-102">Details</span></span>|<span data-ttu-id="5a4a2-103">從 .NET Framework 4.5 開始，在 <xref:System.Web.HttpRequest?displayProperty=name> 本文中禁止使用 UTF-7 編碼。</span><span class="sxs-lookup"><span data-stu-id="5a4a2-103">Beginning in .NET Framework 4.5, UTF-7 encoding is prohibited in <xref:System.Web.HttpRequest?displayProperty=name>s' bodies.</span></span> <span data-ttu-id="5a4a2-104">在某些情況下，倚賴傳入 UTF-7 資料的應用程式資料將無法正確解碼。</span><span class="sxs-lookup"><span data-stu-id="5a4a2-104">Data for applications that depend on incoming UTF-7 data will not decode properly in some cases.</span></span>|
|<span data-ttu-id="5a4a2-105">建議</span><span class="sxs-lookup"><span data-stu-id="5a4a2-105">Suggestion</span></span>|<span data-ttu-id="5a4a2-106">在理想情況下，您應該更新應用程式，不要在 <xref:System.Web.HttpRequest?displayProperty=name> 中使用 UTF-7 編碼。</span><span class="sxs-lookup"><span data-stu-id="5a4a2-106">Ideally, applications should be updated to not use UTF-7 encoding in <xref:System.Web.HttpRequest?displayProperty=name>s.</span></span> <span data-ttu-id="5a4a2-107">或者，您也可以使用 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 項目的 <code>aspnet:AllowUtf7RequestContentEncoding</code> 屬性還原舊版行為。</span><span class="sxs-lookup"><span data-stu-id="5a4a2-107">Alternatively, legacy behavior can be restored by using the <code>aspnet:AllowUtf7RequestContentEncoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) element.</span></span>|
|<span data-ttu-id="5a4a2-108">範圍</span><span class="sxs-lookup"><span data-stu-id="5a4a2-108">Scope</span></span>|<span data-ttu-id="5a4a2-109">Edge</span><span class="sxs-lookup"><span data-stu-id="5a4a2-109">Edge</span></span>|
|<span data-ttu-id="5a4a2-110">版本</span><span class="sxs-lookup"><span data-stu-id="5a4a2-110">Version</span></span>|<span data-ttu-id="5a4a2-111">4.5</span><span class="sxs-lookup"><span data-stu-id="5a4a2-111">4.5</span></span>|
|<span data-ttu-id="5a4a2-112">類型</span><span class="sxs-lookup"><span data-stu-id="5a4a2-112">Type</span></span>|<span data-ttu-id="5a4a2-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="5a4a2-113">Runtime</span></span>|
|<span data-ttu-id="5a4a2-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5a4a2-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

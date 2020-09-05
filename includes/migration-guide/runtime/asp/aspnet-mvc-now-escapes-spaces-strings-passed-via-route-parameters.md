---
ms.openlocfilehash: afbf34710c75d0f0586ddfdb2e7937d8d76d5399
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497067"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="568d7-101">ASP.NET MVC 現在會將透過路由參數傳入之字串中的空格逸出</span><span class="sxs-lookup"><span data-stu-id="568d7-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="568d7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="568d7-102">Details</span></span>

<span data-ttu-id="568d7-103">為了遵守 RFC 2396，從路由填入動作參數時，現在會將路由路徑中的空格逸出。</span><span class="sxs-lookup"><span data-stu-id="568d7-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="568d7-104">因此，雖然 <code>/controller/action/some data</code> 先前會比對路由 <code>/controller/action/{data}</code> 並提供 <code>some data</code> 作為資料參數，但現在會改為提供 <code>some%20data</code>。</span><span class="sxs-lookup"><span data-stu-id="568d7-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="568d7-105">建議</span><span class="sxs-lookup"><span data-stu-id="568d7-105">Suggestion</span></span>

<span data-ttu-id="568d7-106">您應該更新程式碼，以將路由中的字串參數設為未逸出。</span><span class="sxs-lookup"><span data-stu-id="568d7-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="568d7-107">如果需要原始 URI，您可以使用 <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API 來存取。</span><span class="sxs-lookup"><span data-stu-id="568d7-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="568d7-108">名稱</span><span class="sxs-lookup"><span data-stu-id="568d7-108">Name</span></span>    | <span data-ttu-id="568d7-109">值</span><span class="sxs-lookup"><span data-stu-id="568d7-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="568d7-110">範圍</span><span class="sxs-lookup"><span data-stu-id="568d7-110">Scope</span></span>   |<span data-ttu-id="568d7-111">Minor</span><span class="sxs-lookup"><span data-stu-id="568d7-111">Minor</span></span>|
|<span data-ttu-id="568d7-112">版本</span><span class="sxs-lookup"><span data-stu-id="568d7-112">Version</span></span>|<span data-ttu-id="568d7-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="568d7-113">4.5.2</span></span>|
|<span data-ttu-id="568d7-114">類型</span><span class="sxs-lookup"><span data-stu-id="568d7-114">Type</span></span>|<span data-ttu-id="568d7-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="568d7-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="568d7-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="568d7-116">Affected APIs</span></span>

- <xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)>

<!--

#### Affected APIs

- `M:System.Web.Mvc.RouteAttribute.#ctor(System.String)`

-->

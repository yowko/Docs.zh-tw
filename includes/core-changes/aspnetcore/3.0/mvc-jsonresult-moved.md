---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901961"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a><span data-ttu-id="1ee14-101">MVC： JsonResult 移動到微軟.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="1ee14-101">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>

<span data-ttu-id="1ee14-102">`JsonResult`已移動到程式集`Microsoft.AspNetCore.Mvc.Core`。</span><span class="sxs-lookup"><span data-stu-id="1ee14-102">`JsonResult` has moved to the `Microsoft.AspNetCore.Mvc.Core` assembly.</span></span> <span data-ttu-id="1ee14-103">此類型曾經在微軟中定義[。](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json)</span><span class="sxs-lookup"><span data-stu-id="1ee14-103">This type used to be defined in [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json).</span></span> <span data-ttu-id="1ee14-104">向大多數使用者添加了`Microsoft.AspNetCore.Mvc.Formatters.Json`程式集級[[TypeForwardedto]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute)屬性以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="1ee14-104">An assembly-level [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) attribute was added to `Microsoft.AspNetCore.Mvc.Formatters.Json` to address this issue for the majority of users.</span></span> <span data-ttu-id="1ee14-105">使用協力廠商庫的應用可能會遇到問題。</span><span class="sxs-lookup"><span data-stu-id="1ee14-105">Apps that use third-party libraries may encounter issues.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1ee14-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="1ee14-106">Version introduced</span></span>

<span data-ttu-id="1ee14-107">3.0 預覽 6</span><span class="sxs-lookup"><span data-stu-id="1ee14-107">3.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1ee14-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1ee14-108">Old behavior</span></span>

<span data-ttu-id="1ee14-109">使用基於 2.2 的庫的應用成功生成。</span><span class="sxs-lookup"><span data-stu-id="1ee14-109">An app using a 2.2-based library builds successfully.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1ee14-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="1ee14-110">New behavior</span></span>

<span data-ttu-id="1ee14-111">使用基於 2.2 的庫的應用編譯失敗。</span><span class="sxs-lookup"><span data-stu-id="1ee14-111">An app using a 2.2-based library fails compilation.</span></span> <span data-ttu-id="1ee14-112">提供了包含以下文本變體的錯誤：</span><span class="sxs-lookup"><span data-stu-id="1ee14-112">An error containing a variation of the following text is provided:</span></span>

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

<span data-ttu-id="1ee14-113">有關此類問題的示例，請參閱[dotnet/aspnetcore_7220](https://github.com/dotnet/aspnetcore/issues/7220)。</span><span class="sxs-lookup"><span data-stu-id="1ee14-113">For an example of such an issue, see [dotnet/aspnetcore#7220](https://github.com/dotnet/aspnetcore/issues/7220).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1ee14-114">更改原因</span><span class="sxs-lookup"><span data-stu-id="1ee14-114">Reason for change</span></span>

<span data-ttu-id="1ee14-115">ASP.NET核心的組成的平臺級更改，如[aspnet/公告#325](https://github.com/aspnet/Announcements/issues/325)所述。</span><span class="sxs-lookup"><span data-stu-id="1ee14-115">Platform-level changes to the composition of ASP.NET Core as described at [aspnet/Announcements#325](https://github.com/aspnet/Announcements/issues/325).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1ee14-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1ee14-116">Recommended action</span></span>

<span data-ttu-id="1ee14-117">根據 2.2 版本的庫編譯`Microsoft.AspNetCore.Mvc.Formatters.Json`可能需要重新編譯以解決所有消費者的問題。</span><span class="sxs-lookup"><span data-stu-id="1ee14-117">Libraries compiled against the 2.2 version of `Microsoft.AspNetCore.Mvc.Formatters.Json` may need to recompile to address the problem for all consumers.</span></span> <span data-ttu-id="1ee14-118">如果受到影響，請與庫作者聯繫。</span><span class="sxs-lookup"><span data-stu-id="1ee14-118">If affected, contact the library author.</span></span> <span data-ttu-id="1ee14-119">請求重新編譯庫以ASP.NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="1ee14-119">Request recompilation of the library to target ASP.NET Core 3.0.</span></span>

#### <a name="category"></a><span data-ttu-id="1ee14-120">類別</span><span class="sxs-lookup"><span data-stu-id="1ee14-120">Category</span></span>

<span data-ttu-id="1ee14-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1ee14-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1ee14-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1ee14-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->

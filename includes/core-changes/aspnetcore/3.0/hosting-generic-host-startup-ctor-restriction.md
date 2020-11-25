---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032349"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="eaac8-101">裝載：泛型主機限制啟動的函式插入</span><span class="sxs-lookup"><span data-stu-id="eaac8-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="eaac8-102">泛型主機針對類別的函式插入所支援的唯一類型為 `Startup` `IHostEnvironment` 、 `IWebHostEnvironment` 和 `IConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="eaac8-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="eaac8-103">使用的應用程式 `WebHost` 不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="eaac8-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eaac8-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="eaac8-104">Change description</span></span>

<span data-ttu-id="eaac8-105">在 ASP.NET Core 3.0 之前，您可以在類別的函式中，將函式插入用於任意類型 `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="eaac8-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="eaac8-106">在 ASP.NET Core 3.0 中，web 堆疊已 replatformed 至一般主機程式庫。</span><span class="sxs-lookup"><span data-stu-id="eaac8-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="eaac8-107">您可以在範本的 *Program.cs* 檔案中看到變更：</span><span class="sxs-lookup"><span data-stu-id="eaac8-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="eaac8-108">**ASP.NET Core 2.x：**</span><span class="sxs-lookup"><span data-stu-id="eaac8-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="eaac8-109">**ASP.NET Core 3.0：**</span><span class="sxs-lookup"><span data-stu-id="eaac8-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="eaac8-110">`Host` 使用一個相依性插入 (DI) 容器來建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaac8-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="eaac8-111">`WebHost` 使用兩個容器：一個用於主機，另一個用於應用程式。</span><span class="sxs-lookup"><span data-stu-id="eaac8-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="eaac8-112">因此，此函式 `Startup` 不再支援自訂服務插入。</span><span class="sxs-lookup"><span data-stu-id="eaac8-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="eaac8-113">只有 `IHostEnvironment` 、 `IWebHostEnvironment` 和 `IConfiguration` 可以插入。</span><span class="sxs-lookup"><span data-stu-id="eaac8-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="eaac8-114">這項變更可防止 DI 問題（例如重複建立單一服務）。</span><span class="sxs-lookup"><span data-stu-id="eaac8-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eaac8-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="eaac8-115">Version introduced</span></span>

<span data-ttu-id="eaac8-116">3.0</span><span class="sxs-lookup"><span data-stu-id="eaac8-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eaac8-117">變更的原因</span><span class="sxs-lookup"><span data-stu-id="eaac8-117">Reason for change</span></span>

<span data-ttu-id="eaac8-118">這項變更是將 web 堆疊遷移至一般主機程式庫的結果。</span><span class="sxs-lookup"><span data-stu-id="eaac8-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eaac8-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="eaac8-119">Recommended action</span></span>

<span data-ttu-id="eaac8-120">將服務插入方法簽章中 `Startup.Configure` 。</span><span class="sxs-lookup"><span data-stu-id="eaac8-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="eaac8-121">例如：</span><span class="sxs-lookup"><span data-stu-id="eaac8-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="eaac8-122">類別</span><span class="sxs-lookup"><span data-stu-id="eaac8-122">Category</span></span>

<span data-ttu-id="eaac8-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eaac8-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eaac8-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="eaac8-124">Affected APIs</span></span>

<span data-ttu-id="eaac8-125">None</span><span class="sxs-lookup"><span data-stu-id="eaac8-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

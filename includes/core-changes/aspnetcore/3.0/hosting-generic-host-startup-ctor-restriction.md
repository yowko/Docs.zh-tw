---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901820"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="5e699-101">託管：通用主機限制啟動建構函式注入</span><span class="sxs-lookup"><span data-stu-id="5e699-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="5e699-102">類建構函式注入的泛型主機`Startup`支援的唯一類型是`IHostEnvironment``IWebHostEnvironment`和`IConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="5e699-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="5e699-103">使用`WebHost`的應用不受影響。</span><span class="sxs-lookup"><span data-stu-id="5e699-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5e699-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="5e699-104">Change description</span></span>

<span data-ttu-id="5e699-105">在ASP.NET Core 3.0 之前，建構函式注入可用於類建構函式中的`Startup`任意類型。</span><span class="sxs-lookup"><span data-stu-id="5e699-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="5e699-106">在 ASP.NET Core 3.0 中，Web 堆疊重新平臺化到通用主機庫。</span><span class="sxs-lookup"><span data-stu-id="5e699-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="5e699-107">您可以在範本的*Program.cs*檔中看到更改：</span><span class="sxs-lookup"><span data-stu-id="5e699-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="5e699-108">**ASP.NET核心 2.x：**</span><span class="sxs-lookup"><span data-stu-id="5e699-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="5e699-109">**ASP.NET核心 3.0：**</span><span class="sxs-lookup"><span data-stu-id="5e699-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="5e699-110">`Host`使用一個依賴項注入 （DI） 容器來生成應用。</span><span class="sxs-lookup"><span data-stu-id="5e699-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="5e699-111">`WebHost`使用兩個容器：一個用於主機，一個用於應用。</span><span class="sxs-lookup"><span data-stu-id="5e699-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="5e699-112">因此，`Startup`建構函式不再支援自訂服務注入。</span><span class="sxs-lookup"><span data-stu-id="5e699-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="5e699-113">只能`IHostEnvironment`注入`IWebHostEnvironment`，`IConfiguration`並且可以注入。</span><span class="sxs-lookup"><span data-stu-id="5e699-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="5e699-114">此更改可防止 DI 問題，例如重複創建單例服務。</span><span class="sxs-lookup"><span data-stu-id="5e699-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5e699-115">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="5e699-115">Version introduced</span></span>

<span data-ttu-id="5e699-116">3.0</span><span class="sxs-lookup"><span data-stu-id="5e699-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5e699-117">更改原因</span><span class="sxs-lookup"><span data-stu-id="5e699-117">Reason for change</span></span>

<span data-ttu-id="5e699-118">此更改是將 Web 堆疊重新平臺到通用主機庫的結果。</span><span class="sxs-lookup"><span data-stu-id="5e699-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5e699-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5e699-119">Recommended action</span></span>

<span data-ttu-id="5e699-120">將服務注入`Startup.Configure`方法簽名。</span><span class="sxs-lookup"><span data-stu-id="5e699-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="5e699-121">例如：</span><span class="sxs-lookup"><span data-stu-id="5e699-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="5e699-122">類別</span><span class="sxs-lookup"><span data-stu-id="5e699-122">Category</span></span>

<span data-ttu-id="5e699-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5e699-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5e699-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5e699-124">Affected APIs</span></span>

<span data-ttu-id="5e699-125">None</span><span class="sxs-lookup"><span data-stu-id="5e699-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

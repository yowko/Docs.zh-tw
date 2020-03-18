---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394344"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="d3f54-101">標識：更改了 UI 的預設引導版本</span><span class="sxs-lookup"><span data-stu-id="d3f54-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="d3f54-102">從 ASP.NET 酷 3.0 開始，標識 UI 預設使用 Bootstrap 的版本 4。</span><span class="sxs-lookup"><span data-stu-id="d3f54-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3f54-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="d3f54-103">Version introduced</span></span>

<span data-ttu-id="d3f54-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d3f54-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d3f54-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d3f54-105">Old behavior</span></span>

<span data-ttu-id="d3f54-106">方法`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`調用與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="d3f54-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d3f54-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="d3f54-107">New behavior</span></span>

<span data-ttu-id="d3f54-108">方法`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`調用與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="d3f54-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d3f54-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="d3f54-109">Reason for change</span></span>

<span data-ttu-id="d3f54-110">引導 4 在 ASP.NET 核心 3.0 時間幀期間發佈。</span><span class="sxs-lookup"><span data-stu-id="d3f54-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3f54-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d3f54-111">Recommended action</span></span>

<span data-ttu-id="d3f54-112">如果您使用預設標識 UI 並在 中`Startup.ConfigureServices`添加了此更改，則您受到此更改的影響，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="d3f54-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="d3f54-113">請採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="d3f54-113">Take one of the following actions:</span></span>

- <span data-ttu-id="d3f54-114">使用其[遷移指南](https://getbootstrap.com/docs/4.0/migration)遷移應用以使用引導 4。</span><span class="sxs-lookup"><span data-stu-id="d3f54-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="d3f54-115">更新`Startup.ConfigureServices`以強制使用引導 3。</span><span class="sxs-lookup"><span data-stu-id="d3f54-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="d3f54-116">例如：</span><span class="sxs-lookup"><span data-stu-id="d3f54-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="d3f54-117">類別</span><span class="sxs-lookup"><span data-stu-id="d3f54-117">Category</span></span>

<span data-ttu-id="d3f54-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d3f54-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3f54-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d3f54-119">Affected APIs</span></span>

<span data-ttu-id="d3f54-120">None</span><span class="sxs-lookup"><span data-stu-id="d3f54-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

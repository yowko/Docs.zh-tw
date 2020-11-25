---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032373"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="b5fa3-101">身分識別： UI 的預設啟動程式版本已變更</span><span class="sxs-lookup"><span data-stu-id="b5fa3-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="b5fa3-102">從 ASP.NET Core 3.0 開始，身分識別 UI 預設為使用第4版的啟動程式。</span><span class="sxs-lookup"><span data-stu-id="b5fa3-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5fa3-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b5fa3-103">Version introduced</span></span>

<span data-ttu-id="b5fa3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b5fa3-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b5fa3-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b5fa3-105">Old behavior</span></span>

<span data-ttu-id="b5fa3-106">`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`方法呼叫與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="b5fa3-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b5fa3-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="b5fa3-107">New behavior</span></span>

<span data-ttu-id="b5fa3-108">`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`方法呼叫與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="b5fa3-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b5fa3-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b5fa3-109">Reason for change</span></span>

<span data-ttu-id="b5fa3-110">啟動程式4是在 ASP.NET Core 3.0 時間範圍內發行。</span><span class="sxs-lookup"><span data-stu-id="b5fa3-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5fa3-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b5fa3-111">Recommended action</span></span>

<span data-ttu-id="b5fa3-112">如果您使用預設身分識別 UI 並將其加入，則會受到這項變更的影響， `Startup.ConfigureServices` 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b5fa3-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="b5fa3-113">請採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="b5fa3-113">Take one of the following actions:</span></span>

- <span data-ttu-id="b5fa3-114">將您的應用程式遷移至使用啟動程式4，並使用其 [遷移指南](https://getbootstrap.com/docs/4.0/migration)。</span><span class="sxs-lookup"><span data-stu-id="b5fa3-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="b5fa3-115">更新 `Startup.ConfigureServices` 以強制使用啟動程式3。</span><span class="sxs-lookup"><span data-stu-id="b5fa3-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="b5fa3-116">例如：</span><span class="sxs-lookup"><span data-stu-id="b5fa3-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="b5fa3-117">類別</span><span class="sxs-lookup"><span data-stu-id="b5fa3-117">Category</span></span>

<span data-ttu-id="b5fa3-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b5fa3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5fa3-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b5fa3-119">Affected APIs</span></span>

<span data-ttu-id="b5fa3-120">None</span><span class="sxs-lookup"><span data-stu-id="b5fa3-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

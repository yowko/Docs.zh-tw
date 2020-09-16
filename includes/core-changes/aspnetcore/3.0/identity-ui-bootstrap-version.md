---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394344"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="281b4-101">身分識別： UI 的預設啟動程式版本已變更</span><span class="sxs-lookup"><span data-stu-id="281b4-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="281b4-102">從 ASP.NET Core 3.0 開始，身分識別 UI 預設為使用第4版的啟動程式。</span><span class="sxs-lookup"><span data-stu-id="281b4-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="281b4-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="281b4-103">Version introduced</span></span>

<span data-ttu-id="281b4-104">3.0</span><span class="sxs-lookup"><span data-stu-id="281b4-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="281b4-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="281b4-105">Old behavior</span></span>

<span data-ttu-id="281b4-106">`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`方法呼叫與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="281b4-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="281b4-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="281b4-107">New behavior</span></span>

<span data-ttu-id="281b4-108">`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();`方法呼叫與`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="281b4-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="281b4-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="281b4-109">Reason for change</span></span>

<span data-ttu-id="281b4-110">啟動程式4是在 ASP.NET Core 3.0 時間範圍內發行。</span><span class="sxs-lookup"><span data-stu-id="281b4-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="281b4-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="281b4-111">Recommended action</span></span>

<span data-ttu-id="281b4-112">如果您使用預設身分識別 UI 並將其加入，則會受到這項變更的影響， `Startup.ConfigureServices` 如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="281b4-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="281b4-113">請採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="281b4-113">Take one of the following actions:</span></span>

- <span data-ttu-id="281b4-114">將您的應用程式遷移至使用啟動程式4，並使用其 [遷移指南](https://getbootstrap.com/docs/4.0/migration)。</span><span class="sxs-lookup"><span data-stu-id="281b4-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="281b4-115">更新 `Startup.ConfigureServices` 以強制使用啟動程式3。</span><span class="sxs-lookup"><span data-stu-id="281b4-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="281b4-116">例如：</span><span class="sxs-lookup"><span data-stu-id="281b4-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="281b4-117">類別</span><span class="sxs-lookup"><span data-stu-id="281b4-117">Category</span></span>

<span data-ttu-id="281b4-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="281b4-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="281b4-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="281b4-119">Affected APIs</span></span>

<span data-ttu-id="281b4-120">無</span><span class="sxs-lookup"><span data-stu-id="281b4-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

---
title: 功能旗標
description: 利用 Azure App Config 在雲端原生應用程式中執行功能旗標
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: ee45c9f187b056887ea6dd3a08da508afca51987
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158093"
---
# <a name="feature-flags"></a><span data-ttu-id="bdb35-103">功能旗標</span><span class="sxs-lookup"><span data-stu-id="bdb35-103">Feature flags</span></span>

<span data-ttu-id="bdb35-104">在第1章中，我們 affirmed 雲端原生相當於速度和靈活性。</span><span class="sxs-lookup"><span data-stu-id="bdb35-104">In chapter 1, we affirmed that cloud native is much about speed and agility.</span></span> <span data-ttu-id="bdb35-105">使用者預期快速回應性、創新功能和零停機時間。</span><span class="sxs-lookup"><span data-stu-id="bdb35-105">Users expect rapid responsiveness, innovative features, and zero downtime.</span></span> <span data-ttu-id="bdb35-106">`Feature flags` 是新式的部署技術，可協助提高雲端原生應用程式的靈活性。</span><span class="sxs-lookup"><span data-stu-id="bdb35-106">`Feature flags` are a modern deployment technique that helps increase agility for cloud-native applications.</span></span> <span data-ttu-id="bdb35-107">它們可讓您將新功能部署到生產環境中，但限制其可用性。</span><span class="sxs-lookup"><span data-stu-id="bdb35-107">They enable you to deploy new features into a production environment, but restrict their availability.</span></span> <span data-ttu-id="bdb35-108">使用開關的筆勢，您可以為特定使用者啟用新功能，而不需要重新開機應用程式或部署新的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdb35-108">With the flick of a switch, you can activate a new feature for specific users without restarting the app or deploying new code.</span></span> <span data-ttu-id="bdb35-109">它們會將新功能的發行與程式碼部署分開。</span><span class="sxs-lookup"><span data-stu-id="bdb35-109">They separate the release of new features from their code deployment.</span></span>

<span data-ttu-id="bdb35-110">功能旗標是以條件式邏輯為基礎，可在執行時間控制使用者的功能可視性。</span><span class="sxs-lookup"><span data-stu-id="bdb35-110">Feature flags are built upon conditional logic that control visibility of functionality for users at runtime.</span></span> <span data-ttu-id="bdb35-111">在新式的雲端原生系統中，通常會提早將新功能部署到生產環境中，但以有限的物件進行測試。</span><span class="sxs-lookup"><span data-stu-id="bdb35-111">In modern cloud-native systems, it's common to deploy new features into production early, but test them with a limited audience.</span></span> <span data-ttu-id="bdb35-112">當信賴度增加時，可以將此功能以累加方式推出給更廣大的觀眾。</span><span class="sxs-lookup"><span data-stu-id="bdb35-112">As confidence increases, the feature can be incrementally rolled out to wider audiences.</span></span>

<span data-ttu-id="bdb35-113">功能旗標的其他使用案例包括：</span><span class="sxs-lookup"><span data-stu-id="bdb35-113">Other use cases for feature flags include:</span></span>

- <span data-ttu-id="bdb35-114">將 premium 功能限制為願意支付更高訂用帳戶費用的特定客戶群組。</span><span class="sxs-lookup"><span data-stu-id="bdb35-114">Restrict premium functionality to specific customer groups willing to pay higher subscription fees.</span></span>
- <span data-ttu-id="bdb35-115">藉由快速停用問題功能來穩定系統，避免復原或立即修正的風險。</span><span class="sxs-lookup"><span data-stu-id="bdb35-115">Stabilize a system by quickly deactivating a problem feature, avoiding the risks of a rollback or immediate hotfix.</span></span>
- <span data-ttu-id="bdb35-116">在尖峰使用期間停用具有高資源耗用量的選用功能。</span><span class="sxs-lookup"><span data-stu-id="bdb35-116">Disable an optional feature with high resource consumption during peak usage periods.</span></span>
- <span data-ttu-id="bdb35-117">對 `experimental feature releases` 小型使用者區段進行驗證，以驗證可行性和熱門程度。</span><span class="sxs-lookup"><span data-stu-id="bdb35-117">Conduct `experimental feature releases` to small user segments to validate feasibility and popularity.</span></span>

<span data-ttu-id="bdb35-118">功能旗標也會促進 `trunk-based` 開發。</span><span class="sxs-lookup"><span data-stu-id="bdb35-118">Feature flags also promote `trunk-based` development.</span></span> <span data-ttu-id="bdb35-119">它是一種原始檔控制分支模型，開發人員會在此模型中對單一分支中的功能進行共同作業。</span><span class="sxs-lookup"><span data-stu-id="bdb35-119">It's a source-control branching model where developers collaborate on features in a single branch.</span></span> <span data-ttu-id="bdb35-120">此方法可將合併大量長時間執行功能分支的風險和複雜性降至最低。</span><span class="sxs-lookup"><span data-stu-id="bdb35-120">The approach minimizes the risk and complexity of merging large numbers of long-running feature branches.</span></span> <span data-ttu-id="bdb35-121">功能在啟用之前無法使用。</span><span class="sxs-lookup"><span data-stu-id="bdb35-121">Features are unavailable until activated.</span></span>

## <a name="implementing-feature-flags"></a><span data-ttu-id="bdb35-122">執行功能旗標</span><span class="sxs-lookup"><span data-stu-id="bdb35-122">Implementing feature flags</span></span>

<span data-ttu-id="bdb35-123">在其核心中，功能旗標是簡單的參考 `decision object` 。</span><span class="sxs-lookup"><span data-stu-id="bdb35-123">At its core, a feature flag is a reference to a simple `decision object`.</span></span> <span data-ttu-id="bdb35-124">它會傳回或的布林 `on` 狀態 `off` 。</span><span class="sxs-lookup"><span data-stu-id="bdb35-124">It returns a Boolean state of `on` or `off`.</span></span> <span data-ttu-id="bdb35-125">旗標通常會包裝封裝功能功能的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="bdb35-125">The flag typically wraps a block of code that encapsulates a feature capability.</span></span> <span data-ttu-id="bdb35-126">旗標的狀態會決定是否要為指定的使用者執行該程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="bdb35-126">The state of the flag determines whether that code block executes for a given user.</span></span> <span data-ttu-id="bdb35-127">圖10-11 顯示執行。</span><span class="sxs-lookup"><span data-stu-id="bdb35-127">Figure 10-11 shows the implementation.</span></span>

```csharp
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

<span data-ttu-id="bdb35-128">**圖 10-11** -簡單的功能旗標實行。</span><span class="sxs-lookup"><span data-stu-id="bdb35-128">**Figure 10-11** - Simple feature flag implementation.</span></span>

<span data-ttu-id="bdb35-129">請注意這個方法如何分隔決策邏輯與功能程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdb35-129">Note how this approach separates the decision logic from the feature code.</span></span>

<span data-ttu-id="bdb35-130">在第1章中，我們討論過 `Twelve-Factor App` 。</span><span class="sxs-lookup"><span data-stu-id="bdb35-130">In chapter 1, we discussed the `Twelve-Factor App`.</span></span> <span data-ttu-id="bdb35-131">建議在應用程式可執行程式碼外部保留設定設定的指導方針。</span><span class="sxs-lookup"><span data-stu-id="bdb35-131">The guidance recommended keeping configuration settings external from application executable code.</span></span> <span data-ttu-id="bdb35-132">如有需要，可以從外部來源讀取設定。</span><span class="sxs-lookup"><span data-stu-id="bdb35-132">When needed, settings can be read in from the external source.</span></span> <span data-ttu-id="bdb35-133">功能旗標設定值也應該獨立于其程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="bdb35-133">Feature flag configuration values should also be independent from their codebase.</span></span> <span data-ttu-id="bdb35-134">藉由在不同的儲存機制中具體化旗標設定，您可以變更旗標狀態，而不需要修改和重新部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="bdb35-134">By externalizing flag configuration in a separate repository, you can change flag state without modifying and redeploying the application.</span></span>

<span data-ttu-id="bdb35-135">[Azure 應用程式組態](/azure/azure-app-configuration/overview) 提供功能旗標的集中式存放庫。</span><span class="sxs-lookup"><span data-stu-id="bdb35-135">[Azure App Configuration](/azure/azure-app-configuration/overview) provides a centralized repository for feature flags.</span></span> <span data-ttu-id="bdb35-136">使用它，您可以定義不同種類的功能旗標，並快速且安心地操作其狀態。</span><span class="sxs-lookup"><span data-stu-id="bdb35-136">With it, you define different kinds of feature flags and manipulate their states quickly and confidently.</span></span> <span data-ttu-id="bdb35-137">您可以將應用程式設定用戶端程式庫新增至您的應用程式，以啟用功能旗標功能。</span><span class="sxs-lookup"><span data-stu-id="bdb35-137">You add the App Configuration client libraries to your application to enable feature flag functionality.</span></span> <span data-ttu-id="bdb35-138">支援各種程式設計語言架構。</span><span class="sxs-lookup"><span data-stu-id="bdb35-138">Various programming language frameworks are supported.</span></span>

<span data-ttu-id="bdb35-139">功能旗標可以在 [ASP.NET Core 服務](/azure/azure-app-configuration/use-feature-flags-dotnet-core)中輕鬆地執行。</span><span class="sxs-lookup"><span data-stu-id="bdb35-139">Feature flags can be easily implemented in an [ASP.NET Core service](/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span></span> <span data-ttu-id="bdb35-140">安裝 .NET 功能管理程式庫和應用程式設定提供者，可讓您以宣告方式將功能旗標新增至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdb35-140">Installing the .NET Feature Management libraries and App Configuration provider enable you to declaratively add feature flags to your code.</span></span> <span data-ttu-id="bdb35-141">它們可啟用 `FeatureGate` 屬性，讓您不必在程式碼基底中手動寫入 if 語句。</span><span class="sxs-lookup"><span data-stu-id="bdb35-141">They enable `FeatureGate` attributes so that you don't have to manually write if statements across your codebase.</span></span>

<span data-ttu-id="bdb35-142">在啟動類別中設定之後，您可以在控制器、動作或中介軟體層級新增功能旗標功能。</span><span class="sxs-lookup"><span data-stu-id="bdb35-142">Once configured in your Startup class, you can add feature flag functionality at the controller, action, or middleware level.</span></span> <span data-ttu-id="bdb35-143">圖10-12 顯示控制器和動作執行：</span><span class="sxs-lookup"><span data-stu-id="bdb35-143">Figure 10-12 presents controller and action implementation:</span></span>

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

<span data-ttu-id="bdb35-144">**圖 10-12** -控制器和動作中的功能旗標實行。</span><span class="sxs-lookup"><span data-stu-id="bdb35-144">**Figure 10-12** - Feature flag implementation in a controller and action.</span></span>

<span data-ttu-id="bdb35-145">如果停用功能旗標，使用者將會收到 404 (找不到) 狀態碼，且沒有回應主體。</span><span class="sxs-lookup"><span data-stu-id="bdb35-145">If a feature flag is disabled, the user will receive a 404 (Not Found) status code with no response body.</span></span>

<span data-ttu-id="bdb35-146">功能旗標也可以直接插入 c # 類別。</span><span class="sxs-lookup"><span data-stu-id="bdb35-146">Feature flags can also be injected directly into C# classes.</span></span> <span data-ttu-id="bdb35-147">圖10-13 顯示功能旗標插入：</span><span class="sxs-lookup"><span data-stu-id="bdb35-147">Figure 10-13 shows feature flag injection:</span></span>

```csharp
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

<span data-ttu-id="bdb35-148">**圖 10-13** -功能旗標插入類別中。</span><span class="sxs-lookup"><span data-stu-id="bdb35-148">**Figure 10-13** - Feature flag injection into a class.</span></span>

<span data-ttu-id="bdb35-149">功能管理程式庫會管理幕後的功能旗標生命週期。</span><span class="sxs-lookup"><span data-stu-id="bdb35-149">The Feature Management libraries manage the feature flag lifecycle behind the scenes.</span></span> <span data-ttu-id="bdb35-150">例如，為了將大量呼叫設定存放區的次數降到最低，程式庫快取旗標會指出指定的持續時間。</span><span class="sxs-lookup"><span data-stu-id="bdb35-150">For example, to minimize high numbers of calls to the configuration store, the libraries cache flag states for a specified duration.</span></span> <span data-ttu-id="bdb35-151">它們可以保證在要求呼叫期間不會有旗標狀態。</span><span class="sxs-lookup"><span data-stu-id="bdb35-151">They can guarantee the immutability of flag states during a request call.</span></span> <span data-ttu-id="bdb35-152">它們也提供 `Point-in-time snapshot` 。</span><span class="sxs-lookup"><span data-stu-id="bdb35-152">They also offer a `Point-in-time snapshot`.</span></span> <span data-ttu-id="bdb35-153">您可以重建任何索引鍵/值的歷程記錄，並在過去七天內的任何時間都提供其過去的值。</span><span class="sxs-lookup"><span data-stu-id="bdb35-153">You can reconstruct the history of any key-value and provide its past value at any moment within the previous seven days.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bdb35-154">[上一個](devops.md) 
>[下一步](infrastructure-as-code.md)</span><span class="sxs-lookup"><span data-stu-id="bdb35-154">[Previous](devops.md)
[Next](infrastructure-as-code.md)</span></span>

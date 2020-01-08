---
title: Xamarin 限制
ms.date: 12/13/2019
description: 說明您在使用 Xamarin 時會遇到的一些限制。
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447164"
---
# <a name="xamarin-limitations"></a><span data-ttu-id="b98d5-103">Xamarin 限制</span><span class="sxs-lookup"><span data-stu-id="b98d5-103">Xamarin limitations</span></span>

<span data-ttu-id="b98d5-104">.NET Standard 2.0 的 Sqlite 目標，而且 Xamarin 支援。</span><span class="sxs-lookup"><span data-stu-id="b98d5-104">Microsoft.Data.Sqlite targets .NET Standard 2.0 and is supported on Xamarin.</span></span> <span data-ttu-id="b98d5-105">下表顯示預設 SQLitePCLRaw 組合提供原生 SQLite 二進位檔的平臺。</span><span class="sxs-lookup"><span data-stu-id="b98d5-105">The following table shows which platforms the default SQLitePCLRaw bundle provides native SQLite binaries for.</span></span> <span data-ttu-id="b98d5-106">如需使用不同配套的詳細資訊，或提供您自己的原生 SQLite 二進位檔，請參閱[自訂 SQLite 版本](custom-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="b98d5-106">See [Custom SQLite versions](custom-versions.md) for details on using a different bundle or providing your own native SQLite binaries.</span></span>

| <span data-ttu-id="b98d5-107">Platform</span><span class="sxs-lookup"><span data-stu-id="b98d5-107">Platform</span></span> | <span data-ttu-id="b98d5-108">SQLite 二進位檔</span><span class="sxs-lookup"><span data-stu-id="b98d5-108">SQLite binaries</span></span> |
| --- | --- |
| <span data-ttu-id="b98d5-109">**Xamarin.Android**</span><span class="sxs-lookup"><span data-stu-id="b98d5-109">**Xamarin.Android**</span></span> | <span data-ttu-id="b98d5-110">—</span><span class="sxs-lookup"><span data-stu-id="b98d5-110">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | <span data-ttu-id="b98d5-111">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-111">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | <span data-ttu-id="b98d5-112">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-112">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="b98d5-113">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-113">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | <span data-ttu-id="b98d5-114">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-114">✔</span></span> |
| <span data-ttu-id="b98d5-115">**Xamarin.iOS**</span><span class="sxs-lookup"><span data-stu-id="b98d5-115">**Xamarin.iOS**</span></span> | <span data-ttu-id="b98d5-116">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-116">✔</span></span> |
| <span data-ttu-id="b98d5-117">**Xamarin.Mac**</span><span class="sxs-lookup"><span data-stu-id="b98d5-117">**Xamarin.Mac**</span></span> | <span data-ttu-id="b98d5-118">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-118">✔</span></span> |
| <span data-ttu-id="b98d5-119">**TVOS**</span><span class="sxs-lookup"><span data-stu-id="b98d5-119">**Xamarin.TVOS**</span></span> | <span data-ttu-id="b98d5-120">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-120">✔</span></span> |
| <span data-ttu-id="b98d5-121">**UWP**</span><span class="sxs-lookup"><span data-stu-id="b98d5-121">**UWP**</span></span> | <span data-ttu-id="b98d5-122">—</span><span class="sxs-lookup"><span data-stu-id="b98d5-122">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | <span data-ttu-id="b98d5-123">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-123">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | <span data-ttu-id="b98d5-124">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-124">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | <span data-ttu-id="b98d5-125">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-125">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="b98d5-126">✔</span><span class="sxs-lookup"><span data-stu-id="b98d5-126">✔</span></span> |

## <a name="ios"></a><span data-ttu-id="b98d5-127">iOS</span><span class="sxs-lookup"><span data-stu-id="b98d5-127">iOS</span></span>

<span data-ttu-id="b98d5-128">Sqlite 會嘗試自動初始化 SQLitePCLRaw 組合。</span><span class="sxs-lookup"><span data-stu-id="b98d5-128">Microsoft.Data.Sqlite tries to automatically initialize SQLitePCLRaw bundles.</span></span> <span data-ttu-id="b98d5-129">可惜的是，因為 Xamarin 的預先（AOT）編譯有限制，所以嘗試會失敗，而且您會收到下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="b98d5-129">Unfortunately, because of limitations in the ahead-of-time (AOT) compilation for Xamarin.iOS, the attempt fails and you get the following error.</span></span>

> <span data-ttu-id="b98d5-130">您必須呼叫 `SQLitePCL.raw.SetProvider()`。</span><span class="sxs-lookup"><span data-stu-id="b98d5-130">You need to call `SQLitePCL.raw.SetProvider()`.</span></span> <span data-ttu-id="b98d5-131">如果您使用配套套件，可以藉由呼叫 `SQLitePCL.Batteries.Init()`來完成此作業。</span><span class="sxs-lookup"><span data-stu-id="b98d5-131">If you're using a bundle package, this is done by calling `SQLitePCL.Batteries.Init()`.</span></span>

<span data-ttu-id="b98d5-132">若要初始化配套，請將下列程式程式碼新增至您的應用程式，然後再使用 Microsoft. Data Sqlite。</span><span class="sxs-lookup"><span data-stu-id="b98d5-132">To initialize the bundle, add the following line of code to your app before using Microsoft.Data.Sqlite.</span></span>

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a><span data-ttu-id="b98d5-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="b98d5-133">See also</span></span>

* [<span data-ttu-id="b98d5-134">非同步限制</span><span class="sxs-lookup"><span data-stu-id="b98d5-134">Async limitations</span></span>](async.md)
* [<span data-ttu-id="b98d5-135">自訂 SQLite 版本</span><span class="sxs-lookup"><span data-stu-id="b98d5-135">Custom SQLite versions</span></span>](custom-versions.md)

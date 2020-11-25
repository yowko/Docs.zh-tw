---
title: 重大變更： PublishDepsFilePath 行為變更
description: 瞭解 .NET 5.0 中的重大變更，其中單一檔案應用程式的 PublishDepsFilePath MSBuild 屬性是空的。
ms.date: 09/17/2020
ms.openlocfilehash: 70631beff31aa3388e59f3b79875ef437351451a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760806"
---
# <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="82787-103">PublishDepsFilePath 行為變更</span><span class="sxs-lookup"><span data-stu-id="82787-103">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="82787-104">`PublishDepsFilePath`單一檔案應用程式的 MSBuild 屬性是空的。</span><span class="sxs-lookup"><span data-stu-id="82787-104">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="82787-105">此外，針對非單一檔案的應用程式，在稍後的組建中，檔案 *上的deps.js* 可能不會複製到輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="82787-105">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="82787-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="82787-106">Version introduced</span></span>

<span data-ttu-id="82787-107">5.0</span><span class="sxs-lookup"><span data-stu-id="82787-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="82787-108">變更描述</span><span class="sxs-lookup"><span data-stu-id="82787-108">Change description</span></span>

<span data-ttu-id="82787-109">在舊版的 .NET 中， `PublishDepsFilePath` MSBuild 屬性是應用程式在非單一檔案應用程式輸出目錄中的 *deps.js* 檔案路徑，以及單一檔案應用程式之中繼目錄中的路徑。</span><span class="sxs-lookup"><span data-stu-id="82787-109">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="82787-110">從 .NET 5.0 開始， `PublishDepsFilePath` 單一檔案應用程式是空的，而新的 `IntermediateDepsFilePath` 屬性會指定中繼目錄中位置 *上的deps.js* 。</span><span class="sxs-lookup"><span data-stu-id="82787-110">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="82787-111">此外，對於非單一檔案應用程式，檔案 *上的deps.js* 可能不會複製到輸出目錄， (也就是) 指定的路徑， `PublishDepsFilePath` 直到稍後在組建中為止。</span><span class="sxs-lookup"><span data-stu-id="82787-111">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="82787-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="82787-112">Reason for change</span></span>

<span data-ttu-id="82787-113">這項變更的原因有幾個：</span><span class="sxs-lookup"><span data-stu-id="82787-113">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="82787-114">由於發佈邏輯的重構，可支援在 .NET 5 中 [改善的單一檔案應用程式](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) 。</span><span class="sxs-lookup"><span data-stu-id="82787-114">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="82787-115">在單一檔案應用程式中，為了防止在 *deps.js開啟* 後嘗試重寫檔案 *deps.js* 的目標，因此不會以無訊息方式影響應用程式。</span><span class="sxs-lookup"><span data-stu-id="82787-115">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="82787-116">基於這個理由， `PublishDepsFilePath` 單一檔案應用程式是空的。</span><span class="sxs-lookup"><span data-stu-id="82787-116">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="82787-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="82787-117">Recommended action</span></span>

<span data-ttu-id="82787-118">*在檔案上* 重寫deps.js的目標通常應該使用屬性來進行 `IntermediateDepsFilePath` 。</span><span class="sxs-lookup"><span data-stu-id="82787-118">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="82787-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="82787-119">Affected APIs</span></span>

<span data-ttu-id="82787-120">N/A</span><span class="sxs-lookup"><span data-stu-id="82787-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->

---
ms.openlocfilehash: 077eadb05ab16f5cec8817b89bc771de0c94aefa
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679316"
---
### <a name="publishdepsfilepath-behavior-change"></a><span data-ttu-id="d30cb-101">PublishDepsFilePath 行為變更</span><span class="sxs-lookup"><span data-stu-id="d30cb-101">PublishDepsFilePath behavior change</span></span>

<span data-ttu-id="d30cb-102">`PublishDepsFilePath`單一檔案應用程式的 MSBuild 屬性是空的。</span><span class="sxs-lookup"><span data-stu-id="d30cb-102">The `PublishDepsFilePath` MSBuild property is empty for single-file applications.</span></span> <span data-ttu-id="d30cb-103">此外，針對非單一檔案的應用程式，在稍後的組建中，檔案 \* 上的deps.js\* 可能不會複製到輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="d30cb-103">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory until later in the build.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d30cb-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d30cb-104">Version introduced</span></span>

<span data-ttu-id="d30cb-105">5.0</span><span class="sxs-lookup"><span data-stu-id="d30cb-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="d30cb-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="d30cb-106">Change description</span></span>

<span data-ttu-id="d30cb-107">在舊版的 .NET 中， `PublishDepsFilePath` MSBuild 屬性是應用程式在非單一檔案應用程式輸出目錄中的 *deps.js* 檔案路徑，以及單一檔案應用程式之中繼目錄中的路徑。</span><span class="sxs-lookup"><span data-stu-id="d30cb-107">In previous .NET versions, the `PublishDepsFilePath` MSBuild property is the path to the app's *deps.json* file in the output directory for non single-file applications, and a path in the intermediate directory for single-file apps.</span></span>

<span data-ttu-id="d30cb-108">從 .NET 5.0 開始， `PublishDepsFilePath` 單一檔案應用程式是空的，而新的 `IntermediateDepsFilePath` 屬性會指定中繼目錄中位置 \* 上的deps.js\* 。</span><span class="sxs-lookup"><span data-stu-id="d30cb-108">Starting in .NET 5.0, `PublishDepsFilePath` is empty for single-file applications and a new `IntermediateDepsFilePath` property specifies the *deps.json* location in the intermediate directory.</span></span> <span data-ttu-id="d30cb-109">此外，對於非單一檔案應用程式，檔案 \* 上的deps.js\* 可能不會複製到輸出目錄， (也就是) 指定的路徑， `PublishDepsFilePath` 直到稍後在組建中為止。</span><span class="sxs-lookup"><span data-stu-id="d30cb-109">Additionally, for non single-file applications, the *deps.json* file may not be copied to the output directory (that is, the path specified by `PublishDepsFilePath`) until later in the build.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d30cb-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d30cb-110">Reason for change</span></span>

<span data-ttu-id="d30cb-111">這項變更的原因有幾個：</span><span class="sxs-lookup"><span data-stu-id="d30cb-111">This change was made for a couple of reasons:</span></span>

- <span data-ttu-id="d30cb-112">由於發佈邏輯的重構，可支援在 .NET 5 中 [改善的單一檔案應用程式](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) 。</span><span class="sxs-lookup"><span data-stu-id="d30cb-112">Due to a refactoring of the publish logic in order to support [improved single-file apps](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md) in .NET 5.</span></span>

- <span data-ttu-id="d30cb-113">在單一檔案應用程式中，為了防止在*deps.js開啟*後嘗試重寫檔案*deps.js*的目標，因此不會以無訊息方式影響應用程式。</span><span class="sxs-lookup"><span data-stu-id="d30cb-113">In single-file apps, to help guard against targets that try to rewrite the *deps.json* file after *deps.json* has already been bundled, thus silently not affecting the app.</span></span> <span data-ttu-id="d30cb-114">基於這個理由， `PublishDepsFilePath` 單一檔案應用程式是空的。</span><span class="sxs-lookup"><span data-stu-id="d30cb-114">For this reason, `PublishDepsFilePath` is empty for single-file applications.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d30cb-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d30cb-115">Recommended action</span></span>

<span data-ttu-id="d30cb-116">*在檔案上*重寫deps.js的目標通常應該使用屬性來進行 `IntermediateDepsFilePath` 。</span><span class="sxs-lookup"><span data-stu-id="d30cb-116">Targets that rewrite the *deps.json* file should generally do so using the `IntermediateDepsFilePath` property.</span></span>

#### <a name="category"></a><span data-ttu-id="d30cb-117">類別</span><span class="sxs-lookup"><span data-stu-id="d30cb-117">Category</span></span>

<span data-ttu-id="d30cb-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="d30cb-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d30cb-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d30cb-119">Affected APIs</span></span>

<span data-ttu-id="d30cb-120">N/A</span><span class="sxs-lookup"><span data-stu-id="d30cb-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

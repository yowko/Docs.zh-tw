---
ms.openlocfilehash: c090e99cd0569a843a4c505ad11b8da5740213e8
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440472"
---
### <a name="blazor-updated-validation-logic-for-static-web-assets"></a><span data-ttu-id="d0012-101">Blazor：已更新靜態 web 資產的驗證邏輯</span><span class="sxs-lookup"><span data-stu-id="d0012-101">Blazor: Updated validation logic for static web assets</span></span>

<span data-ttu-id="d0012-102">ASP.NET Core 3.1 和 Blazor WebAssembly 3.2 中的靜態 web 資產發生衝突驗證時發生問題。</span><span class="sxs-lookup"><span data-stu-id="d0012-102">There was an issue in conflict validation for static web assets in ASP.NET Core 3.1 and Blazor WebAssembly 3.2.</span></span> <span data-ttu-id="d0012-103">問題：</span><span class="sxs-lookup"><span data-stu-id="d0012-103">The issue:</span></span>

* <span data-ttu-id="d0012-104">從 Razor 類別庫 (RCLs) 和 Blazor WebAssembly 應用程式之間，防止主機資產和資產之間有適當的衝突偵測。</span><span class="sxs-lookup"><span data-stu-id="d0012-104">Prevented proper conflict detection between the host assets and assets from Razor Class Libraries (RCLs) and Blazor WebAssembly apps.</span></span>
* <span data-ttu-id="d0012-105">大部分會影響 Blazor WebAssembly 應用程式，因為在預設情況下，RCLs 中的靜態 web 資產會在前置詞下提供服務 `_content/$(PackageId)` 。</span><span class="sxs-lookup"><span data-stu-id="d0012-105">Mostly affects Blazor WebAssembly apps, since by default, static web assets in RCLs are served under the `_content/$(PackageId)` prefix.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d0012-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d0012-106">Version introduced</span></span>

<span data-ttu-id="d0012-107">5.0</span><span class="sxs-lookup"><span data-stu-id="d0012-107">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d0012-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="d0012-108">Old behavior</span></span>

<span data-ttu-id="d0012-109">在開發期間，RCL 的靜態 web 資產可能會以無訊息方式在相同主機路徑上以主專案資產覆寫。</span><span class="sxs-lookup"><span data-stu-id="d0012-109">During development, an RCL's static web assets could be silently overridden with host project assets on the same host path.</span></span> <span data-ttu-id="d0012-110">請考慮已定義要在 */folder/file.txt* 提供服務之靜態 web 資產的 RCL。</span><span class="sxs-lookup"><span data-stu-id="d0012-110">Consider an RCL that has defined a static web asset to be served at */folder/file.txt*.</span></span> <span data-ttu-id="d0012-111">如果主機將檔案放在 *wwwroot/資料夾/file.txt* ，伺服器上的檔案會以無訊息方式已覆寫 RCL 或 Blazor WebAssembly 應用程式上的檔案。</span><span class="sxs-lookup"><span data-stu-id="d0012-111">If the host placed a file at *wwwroot/folder/file.txt* , the file on the server silently overrode the file on the RCL or Blazor WebAssembly app.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d0012-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="d0012-112">New behavior</span></span>

<span data-ttu-id="d0012-113">ASP.NET Core 正確地偵測到此問題發生的時間。</span><span class="sxs-lookup"><span data-stu-id="d0012-113">ASP.NET Core correctly detects when this issue happens.</span></span> <span data-ttu-id="d0012-114">它會通知您（使用者）衝突，讓您可以採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="d0012-114">It informs you, the user, of the conflict so that you can take the appropriate action.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d0012-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="d0012-115">Reason for change</span></span>

<span data-ttu-id="d0012-116">靜態 web 資產不會被專案的 *wwwroot* 主機上的檔案覆寫。</span><span class="sxs-lookup"><span data-stu-id="d0012-116">Static web assets weren't intended to be overridable by files on the *wwwroot* host of the project.</span></span> <span data-ttu-id="d0012-117">允許覆寫這些檔案可能會導致難以診斷的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d0012-117">Allowing for the overriding of those files could lead to errors that are difficult to diagnose.</span></span> <span data-ttu-id="d0012-118">結果可能是已發佈應用程式中未定義的行為變更。</span><span class="sxs-lookup"><span data-stu-id="d0012-118">The result could be undefined behavior changes in published apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d0012-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d0012-119">Recommended action</span></span>

<span data-ttu-id="d0012-120">根據預設，RCL 檔不會與主機上的檔案發生衝突。</span><span class="sxs-lookup"><span data-stu-id="d0012-120">By default, there's no reason for an RCL file to conflict with a file on the host.</span></span> <span data-ttu-id="d0012-121">RCL 檔案前面會加上 `_content/${PackageId}` 。</span><span class="sxs-lookup"><span data-stu-id="d0012-121">RCL files are prefixed with `_content/${PackageId}`.</span></span> <span data-ttu-id="d0012-122">Blazor WebAssembly 檔會放在主機 URL 空間的根目錄中，這樣會更容易發生衝突。</span><span class="sxs-lookup"><span data-stu-id="d0012-122">Blazor WebAssembly files are placed at the root of the host URL space, which makes conflicts easier.</span></span> <span data-ttu-id="d0012-123">例如，Blazor WebAssembly apps 包含 *favicon .ico* 檔案，該檔案的主機也可能包含在它的 *wwwroot* 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="d0012-123">For example, Blazor WebAssembly apps contain a *favicon.ico* file that the host might also include in its *wwwroot* folder.</span></span>

<span data-ttu-id="d0012-124">如果衝突的來源是 RCL 檔案，通常表示程式碼正在將資產從程式庫複製到專案的 *wwwroot* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d0012-124">If the conflict's source is an RCL file, it often means code is copying assets from the library into the project's *wwwroot* folder.</span></span> <span data-ttu-id="d0012-125">撰寫程式碼來複製檔案，會破壞靜態 web 資產的主要目標。</span><span class="sxs-lookup"><span data-stu-id="d0012-125">Writing code to copy files defeats a primary goal of static web assets.</span></span> <span data-ttu-id="d0012-126">這是在更新內容而不需要觸發新的編譯時，在瀏覽器上取得更新的基本概念。</span><span class="sxs-lookup"><span data-stu-id="d0012-126">This goal is fundamental to get updates on the browser when the contents are updated without having to trigger a new compilation.</span></span>

<span data-ttu-id="d0012-127">您可以選擇保留這種行為，並維護主機上的檔案。</span><span class="sxs-lookup"><span data-stu-id="d0012-127">You may choose to preserve this behavior and maintain the file on the host.</span></span> <span data-ttu-id="d0012-128">若要這樣做，請從具有自訂 MSBuild 目標的靜態 web 資產清單中移除該檔案。</span><span class="sxs-lookup"><span data-stu-id="d0012-128">To do so, remove the file from the list of static web assets with a custom MSBuild target.</span></span>

<span data-ttu-id="d0012-129">若要使用 RCL 的檔案或 Blazor WebAssembly 應用程式的檔案，而不是主專案的檔案，請從主專案中移除該檔案。</span><span class="sxs-lookup"><span data-stu-id="d0012-129">To use the RCL's file or the Blazor WebAssembly app's file instead of the host project's file, remove the file from the host project.</span></span>

#### <a name="category"></a><span data-ttu-id="d0012-130">類別</span><span class="sxs-lookup"><span data-stu-id="d0012-130">Category</span></span>

<span data-ttu-id="d0012-131">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d0012-131">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d0012-132">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d0012-132">Affected APIs</span></span>

<span data-ttu-id="d0012-133">無</span><span class="sxs-lookup"><span data-stu-id="d0012-133">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

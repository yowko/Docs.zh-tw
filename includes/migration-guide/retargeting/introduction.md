## <a name="introduction"></a><span data-ttu-id="b0e08-101">簡介</span><span class="sxs-lookup"><span data-stu-id="b0e08-101">Introduction</span></span>
<span data-ttu-id="b0e08-102">重定目標變更會影響以其他 .NET Framework 為目標重新編譯的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0e08-102">Retargeting changes affect apps that are recompiled to target a different .NET Framework.</span></span> <span data-ttu-id="b0e08-103">包括：</span><span class="sxs-lookup"><span data-stu-id="b0e08-103">They include:</span></span>

* <span data-ttu-id="b0e08-104">設計階段環境中的變更。</span><span class="sxs-lookup"><span data-stu-id="b0e08-104">Changes in the design-time environment.</span></span> <span data-ttu-id="b0e08-105">例如，建置工具可能會發出之前未發出的警告。</span><span class="sxs-lookup"><span data-stu-id="b0e08-105">For example, build tools may emit warnings when previously they did not.</span></span>

* <span data-ttu-id="b0e08-106">執行階段環境中的變更。</span><span class="sxs-lookup"><span data-stu-id="b0e08-106">Changes in the runtime environment.</span></span> <span data-ttu-id="b0e08-107">這些變更只會影響專以重定目標之 .NET Framework 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0e08-107">These affect only apps that specifically target the retargeted .NET Framework.</span></span> <span data-ttu-id="b0e08-108">針對舊版 .NET Framework 之應用程式的行為，就像是在這些版本下執行的行為一樣。</span><span class="sxs-lookup"><span data-stu-id="b0e08-108">Apps that target previous versions of the .NET Framework behave as they did when running under those versions.</span></span>

<span data-ttu-id="b0e08-109">在描述重定目標變更的主題中，我們會依每個項目的預期影響將項目分類如下：</span><span class="sxs-lookup"><span data-stu-id="b0e08-109">In the topics that describe retargeting changes, we have classified individual items by their expected impact, as follows:</span></span>

<span data-ttu-id="b0e08-110">**重大**這是影響大量應用程式或需要大幅修改程式碼的重大變更。</span><span class="sxs-lookup"><span data-stu-id="b0e08-110">**Major** This is a significant change that affects a large number of apps or that requires substantial modification of code.</span></span>

<span data-ttu-id="b0e08-111">**輕微** 這是影響少量應用程式或需要稍微修改程式碼的變更。</span><span class="sxs-lookup"><span data-stu-id="b0e08-111">**Minor** This is a change that affects a small number of apps or that requires minor modification of code.</span></span>

<span data-ttu-id="b0e08-112">**邊緣案例** 這是在非常特定 (罕見) 的情況下影響應用程式的變更。</span><span class="sxs-lookup"><span data-stu-id="b0e08-112">**Edge case** This is a change that affects apps under very specific scenarios that are not common.</span></span>

<span data-ttu-id="b0e08-113">**透明** 此變更對應用程式的開發人員或使用者的影響不明顯。</span><span class="sxs-lookup"><span data-stu-id="b0e08-113">**Transparent** This is a change that has no noticeable effect on the app's developer or user.</span></span> <span data-ttu-id="b0e08-114">發生此變更的應用程式應該不需要修改。</span><span class="sxs-lookup"><span data-stu-id="b0e08-114">The app should not require modification because of this change.</span></span>

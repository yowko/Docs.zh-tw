---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619995"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="20433-101">WinRT 資料流配接器不會再於關閉時自動呼叫 FlushAsync</span><span class="sxs-lookup"><span data-stu-id="20433-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="20433-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="20433-102">Details</span></span>

<span data-ttu-id="20433-103">在 Windows 市集應用程式中，Windows 執行階段資料流配接器不會再從 Dispose 方法呼叫 FlushAsync 方法。</span><span class="sxs-lookup"><span data-stu-id="20433-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="20433-104">建議</span><span class="sxs-lookup"><span data-stu-id="20433-104">Suggestion</span></span>

<span data-ttu-id="20433-105">這項變更應該是透明的。</span><span class="sxs-lookup"><span data-stu-id="20433-105">This change should be transparent.</span></span> <span data-ttu-id="20433-106">開發人員可以撰寫下列程式碼來還原舊有行為：</span><span class="sxs-lookup"><span data-stu-id="20433-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="20433-107">名稱</span><span class="sxs-lookup"><span data-stu-id="20433-107">Name</span></span>    | <span data-ttu-id="20433-108">值</span><span class="sxs-lookup"><span data-stu-id="20433-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="20433-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="20433-109">Scope</span></span>   |<span data-ttu-id="20433-110">透明</span><span class="sxs-lookup"><span data-stu-id="20433-110">Transparent</span></span>|
|<span data-ttu-id="20433-111">版本</span><span class="sxs-lookup"><span data-stu-id="20433-111">Version</span></span>|<span data-ttu-id="20433-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="20433-112">4.5.1</span></span>|
|<span data-ttu-id="20433-113">類型</span><span class="sxs-lookup"><span data-stu-id="20433-113">Type</span></span>|<span data-ttu-id="20433-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="20433-114">Runtime</span></span>|

---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803538"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="6889f-101">WinRT 資料流配接器不會再於關閉時自動呼叫 FlushAsync</span><span class="sxs-lookup"><span data-stu-id="6889f-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6889f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6889f-102">Details</span></span>|<span data-ttu-id="6889f-103">在 Windows 市集應用程式中，Windows 執行階段資料流配接器不會再從 Dispose 方法呼叫 FlushAsync 方法。</span><span class="sxs-lookup"><span data-stu-id="6889f-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="6889f-104">建議</span><span class="sxs-lookup"><span data-stu-id="6889f-104">Suggestion</span></span>|<span data-ttu-id="6889f-105">這項變更應該是透明的。</span><span class="sxs-lookup"><span data-stu-id="6889f-105">This change should be transparent.</span></span> <span data-ttu-id="6889f-106">開發人員可以撰寫下列程式碼來還原舊有行為：</span><span class="sxs-lookup"><span data-stu-id="6889f-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="6889f-107">範圍</span><span class="sxs-lookup"><span data-stu-id="6889f-107">Scope</span></span>|<span data-ttu-id="6889f-108">透明</span><span class="sxs-lookup"><span data-stu-id="6889f-108">Transparent</span></span>|
|<span data-ttu-id="6889f-109">版本</span><span class="sxs-lookup"><span data-stu-id="6889f-109">Version</span></span>|<span data-ttu-id="6889f-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6889f-110">4.5.1</span></span>|
|<span data-ttu-id="6889f-111">類型</span><span class="sxs-lookup"><span data-stu-id="6889f-111">Type</span></span>|<span data-ttu-id="6889f-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="6889f-112">Runtime</span></span>|

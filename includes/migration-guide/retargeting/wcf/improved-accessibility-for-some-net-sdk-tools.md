---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760203"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="b89c7-101">某些 .NET SDK 工具之改善的協助工具</span><span class="sxs-lookup"><span data-stu-id="b89c7-101">Improved accessibility for some .NET SDK tools</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b89c7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b89c7-102">Details</span></span>|<span data-ttu-id="b89c7-103">在 .NET Framework SDK 4.7.1 中，SvcConfigEditor.exe 和 SvcTraceViewer.exe 工具已透過修正不同的協助工具問題而得到改善。</span><span class="sxs-lookup"><span data-stu-id="b89c7-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="b89c7-104">其中大部分是小問題，例如未定義名稱，或未正確實作某些 UI 自動化模式。</span><span class="sxs-lookup"><span data-stu-id="b89c7-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="b89c7-105">雖然許多使用者並未注意到這些不正確的值，但使用螢幕助讀程式等輔助技術的客戶會發現這些 SDK 工具更易於存取。</span><span class="sxs-lookup"><span data-stu-id="b89c7-105">While many users wouldn’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="b89c7-106">當然，這些修正程式會變更一些先前的行為，例如鍵盤焦點順序。為了取得這些工具的所有協助工具修正程式，您可以將下列程式碼新增至 app.config 檔案：</span><span class="sxs-lookup"><span data-stu-id="b89c7-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="b89c7-107">範圍</span><span class="sxs-lookup"><span data-stu-id="b89c7-107">Scope</span></span>|<span data-ttu-id="b89c7-108">Edge</span><span class="sxs-lookup"><span data-stu-id="b89c7-108">Edge</span></span>|
|<span data-ttu-id="b89c7-109">版本</span><span class="sxs-lookup"><span data-stu-id="b89c7-109">Version</span></span>|<span data-ttu-id="b89c7-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="b89c7-110">4.7.1</span></span>|
|<span data-ttu-id="b89c7-111">類型</span><span class="sxs-lookup"><span data-stu-id="b89c7-111">Type</span></span>|<span data-ttu-id="b89c7-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="b89c7-112">Retargeting</span></span>|


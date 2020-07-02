---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614385"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="d075d-101">某些 .NET SDK 工具之改善的協助工具</span><span class="sxs-lookup"><span data-stu-id="d075d-101">Improved accessibility for some .NET SDK tools</span></span>

#### <a name="details"></a><span data-ttu-id="d075d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d075d-102">Details</span></span>

<span data-ttu-id="d075d-103">在 .NET Framework SDK 4.7.1 中，SvcConfigEditor.exe 和 SvcTraceViewer.exe 工具已透過修正不同的協助工具問題而得到改善。</span><span class="sxs-lookup"><span data-stu-id="d075d-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="d075d-104">其中大部分是小問題，例如未定義名稱，或未正確實作某些 UI 自動化模式。</span><span class="sxs-lookup"><span data-stu-id="d075d-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="d075d-105">雖然許多使用者不會察覺到這些不正確的值，但使用螢幕讀取器等輔助技術的客戶會發現這些 SDK 工具更容易存取。</span><span class="sxs-lookup"><span data-stu-id="d075d-105">While many users wouldn't be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="d075d-106">當然，這些修正程式會變更一些先前的行為，例如鍵盤焦點順序。為了取得這些工具的所有協助工具修正程式，您可以將下列程式碼新增至 app.config 檔案：</span><span class="sxs-lookup"><span data-stu-id="d075d-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| <span data-ttu-id="d075d-107">名稱</span><span class="sxs-lookup"><span data-stu-id="d075d-107">Name</span></span>    | <span data-ttu-id="d075d-108">值</span><span class="sxs-lookup"><span data-stu-id="d075d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d075d-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d075d-109">Scope</span></span>   | <span data-ttu-id="d075d-110">Edge</span><span class="sxs-lookup"><span data-stu-id="d075d-110">Edge</span></span>        |
| <span data-ttu-id="d075d-111">版本</span><span class="sxs-lookup"><span data-stu-id="d075d-111">Version</span></span> | <span data-ttu-id="d075d-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d075d-112">4.7.1</span></span>       |
| <span data-ttu-id="d075d-113">類型</span><span class="sxs-lookup"><span data-stu-id="d075d-113">Type</span></span>    | <span data-ttu-id="d075d-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="d075d-114">Retargeting</span></span> |

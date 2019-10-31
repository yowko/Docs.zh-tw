---
ms.openlocfilehash: 84b6bfc32f5a73597b227098e5aee1e3450cf85b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198373"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="3c32e-101">不支援 EnableVisualStyleValidation 相容性參數</span><span class="sxs-lookup"><span data-stu-id="3c32e-101">Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="3c32e-102">.NET Core 3.0 的 Windows Forms 不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數。</span><span class="sxs-lookup"><span data-stu-id="3c32e-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3c32e-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="3c32e-103">Change description</span></span>

<span data-ttu-id="3c32e-104">在 .NET Framework 中，`Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="3c32e-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="3c32e-105">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 參數。</span><span class="sxs-lookup"><span data-stu-id="3c32e-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3c32e-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3c32e-106">Version introduced</span></span>

<span data-ttu-id="3c32e-107">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="3c32e-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3c32e-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3c32e-108">Recommended action</span></span>

<span data-ttu-id="3c32e-109">移除參數。</span><span class="sxs-lookup"><span data-stu-id="3c32e-109">Remove the switch.</span></span> <span data-ttu-id="3c32e-110">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="3c32e-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="3c32e-111">Category</span><span class="sxs-lookup"><span data-stu-id="3c32e-111">Category</span></span>

<span data-ttu-id="3c32e-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3c32e-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3c32e-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3c32e-113">Affected APIs</span></span>

- <span data-ttu-id="3c32e-114">None</span><span class="sxs-lookup"><span data-stu-id="3c32e-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

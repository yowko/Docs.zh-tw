---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937049"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="838e2-101">不支援啟用視覺化樣式驗證相容性開關</span><span class="sxs-lookup"><span data-stu-id="838e2-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="838e2-102">.NET `Switch.System.Windows.Forms.EnableVisualStyleValidation` Core 3.0 上的 Windows 表單不支援相容性開關。</span><span class="sxs-lookup"><span data-stu-id="838e2-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="838e2-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="838e2-103">Change description</span></span>

<span data-ttu-id="838e2-104">在 .NET 框架`Switch.System.Windows.Forms.EnableVisualStyleValidation`中，相容性開關允許應用程式選擇不驗證以數位形式提供的可視樣式。</span><span class="sxs-lookup"><span data-stu-id="838e2-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="838e2-105">在 .NET 內核`Switch.System.Windows.Forms.EnableVisualStyleValidation`中，不支援交換器。</span><span class="sxs-lookup"><span data-stu-id="838e2-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="838e2-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="838e2-106">Version introduced</span></span>

<span data-ttu-id="838e2-107">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="838e2-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="838e2-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="838e2-108">Recommended action</span></span>

<span data-ttu-id="838e2-109">卸下開關。</span><span class="sxs-lookup"><span data-stu-id="838e2-109">Remove the switch.</span></span> <span data-ttu-id="838e2-110">不支援該開關，並且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="838e2-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="838e2-111">類別</span><span class="sxs-lookup"><span data-stu-id="838e2-111">Category</span></span>

<span data-ttu-id="838e2-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="838e2-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="838e2-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="838e2-113">Affected APIs</span></span>

- <span data-ttu-id="838e2-114">None</span><span class="sxs-lookup"><span data-stu-id="838e2-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

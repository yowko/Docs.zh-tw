---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721321"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="d55c9-101">不支援 EnableVisualStyleValidation 相容性切換</span><span class="sxs-lookup"><span data-stu-id="d55c9-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="d55c9-102">`Switch.System.Windows.Forms.EnableVisualStyleValidation`.Net Core 3.0 的 Windows Forms 不支援相容性參數。</span><span class="sxs-lookup"><span data-stu-id="d55c9-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d55c9-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="d55c9-103">Change description</span></span>

<span data-ttu-id="d55c9-104">在 .NET Framework 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="d55c9-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="d55c9-105">在 .NET Core 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 不支援參數。</span><span class="sxs-lookup"><span data-stu-id="d55c9-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d55c9-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d55c9-106">Version introduced</span></span>

<span data-ttu-id="d55c9-107">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d55c9-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d55c9-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="d55c9-108">Recommended action</span></span>

<span data-ttu-id="d55c9-109">移除參數。</span><span class="sxs-lookup"><span data-stu-id="d55c9-109">Remove the switch.</span></span> <span data-ttu-id="d55c9-110">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="d55c9-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d55c9-111">類別</span><span class="sxs-lookup"><span data-stu-id="d55c9-111">Category</span></span>

<span data-ttu-id="d55c9-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d55c9-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d55c9-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d55c9-113">Affected APIs</span></span>

- <span data-ttu-id="d55c9-114">無</span><span class="sxs-lookup"><span data-stu-id="d55c9-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->

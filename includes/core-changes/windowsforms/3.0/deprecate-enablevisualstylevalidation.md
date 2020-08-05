---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556141"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="bb1da-101">不支援 EnableVisualStyleValidation 相容性切換</span><span class="sxs-lookup"><span data-stu-id="bb1da-101">EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="bb1da-102">在 `Switch.System.Windows.Forms.EnableVisualStyleValidation` .Net Core 或 .net 5.0 和更新版本的 Windows Forms 中不支援相容性參數。</span><span class="sxs-lookup"><span data-stu-id="bb1da-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core or .NET 5.0 and later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bb1da-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="bb1da-103">Change description</span></span>

<span data-ttu-id="bb1da-104">在 .NET Framework 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="bb1da-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="bb1da-105">在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 不支援此參數。</span><span class="sxs-lookup"><span data-stu-id="bb1da-105">In .NET Core and .NET 5.0 and later, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb1da-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bb1da-106">Version introduced</span></span>

<span data-ttu-id="bb1da-107">3.0</span><span class="sxs-lookup"><span data-stu-id="bb1da-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bb1da-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bb1da-108">Recommended action</span></span>

<span data-ttu-id="bb1da-109">移除參數。</span><span class="sxs-lookup"><span data-stu-id="bb1da-109">Remove the switch.</span></span> <span data-ttu-id="bb1da-110">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="bb1da-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="bb1da-111">類別</span><span class="sxs-lookup"><span data-stu-id="bb1da-111">Category</span></span>

<span data-ttu-id="bb1da-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb1da-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb1da-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bb1da-113">Affected APIs</span></span>

- <span data-ttu-id="bb1da-114">無</span><span class="sxs-lookup"><span data-stu-id="bb1da-114">None</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->

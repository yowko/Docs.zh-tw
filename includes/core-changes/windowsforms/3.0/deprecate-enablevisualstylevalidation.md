---
ms.openlocfilehash: 84b6bfc32f5a73597b227098e5aee1e3450cf85b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644009"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a><span data-ttu-id="ab302-101">不支援 EnableVisualStyleValidation 相容性參數</span><span class="sxs-lookup"><span data-stu-id="ab302-101">Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported</span></span>

<span data-ttu-id="ab302-102">.NET Core 3.0 的 Windows Forms 不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數。</span><span class="sxs-lookup"><span data-stu-id="ab302-102">The `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ab302-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ab302-103">Change description</span></span>

<span data-ttu-id="ab302-104">在 .NET Framework 中，`Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。</span><span class="sxs-lookup"><span data-stu-id="ab302-104">In .NET Framework, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` compatibility switch allowed an application to opt out of validation of visual styles supplied in a numeric form.</span></span>

<span data-ttu-id="ab302-105">在 .NET Core 中，不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 參數。</span><span class="sxs-lookup"><span data-stu-id="ab302-105">In .NET Core, the `Switch.System.Windows.Forms.EnableVisualStyleValidation` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ab302-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ab302-106">Version introduced</span></span>

<span data-ttu-id="ab302-107">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="ab302-107">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ab302-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ab302-108">Recommended action</span></span>

<span data-ttu-id="ab302-109">移除參數。</span><span class="sxs-lookup"><span data-stu-id="ab302-109">Remove the switch.</span></span> <span data-ttu-id="ab302-110">不支援此參數，而且沒有可用的替代功能。</span><span class="sxs-lookup"><span data-stu-id="ab302-110">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="ab302-111">Category</span><span class="sxs-lookup"><span data-stu-id="ab302-111">Category</span></span>

<span data-ttu-id="ab302-112">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="ab302-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ab302-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ab302-113">Affected APIs</span></span>

- <span data-ttu-id="ab302-114">None</span><span class="sxs-lookup"><span data-stu-id="ab302-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

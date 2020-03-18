---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644044"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="af549-101">更改可訪問物件的訪問. 運行時 ID 第一專案</span><span class="sxs-lookup"><span data-stu-id="af549-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="af549-102">從 .NET Core 3.0 RC1`AccessibleObject.RuntimeIDFirstItem`開始，的`protected`可`internal`訪問性從 更改為 。</span><span class="sxs-lookup"><span data-stu-id="af549-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="af549-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="af549-103">Change description</span></span>

<span data-ttu-id="af549-104">從 .NET 核心 3.0 預覽`AccessibleObject.RuntimeIDFirstItem`4`protected`開始，該欄位為 。</span><span class="sxs-lookup"><span data-stu-id="af549-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="af549-105">從 .NET Core 3.0 RC1 開始`protected`，`internal`它已更改為 與 .NET 框架中欄位的可訪問性一致。</span><span class="sxs-lookup"><span data-stu-id="af549-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="af549-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="af549-106">Version introduced</span></span>

<span data-ttu-id="af549-107">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="af549-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="af549-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="af549-108">Recommended action</span></span>

<span data-ttu-id="af549-109">如果您開發了 .NET Core 應用，其類型派生自<xref:System.Windows.Forms.AccessibleObject>並訪問`RuntimeIDFirstItem`該欄位，則更改可能會影響您。</span><span class="sxs-lookup"><span data-stu-id="af549-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="af549-110">如果是這種情況，您可以定義本地常量，如下所示：</span><span class="sxs-lookup"><span data-stu-id="af549-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="af549-111">類別</span><span class="sxs-lookup"><span data-stu-id="af549-111">Category</span></span>

<span data-ttu-id="af549-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="af549-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="af549-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="af549-113">Affected APIs</span></span>

- <span data-ttu-id="af549-114">無法通過 API 分析檢測。</span><span class="sxs-lookup"><span data-stu-id="af549-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

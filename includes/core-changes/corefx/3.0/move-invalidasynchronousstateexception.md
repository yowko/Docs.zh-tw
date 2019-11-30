---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568153"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="46647-101">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="46647-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="46647-102">已移動 <xref:System.ComponentModel.InvalidAsynchronousStateException> 類別。</span><span class="sxs-lookup"><span data-stu-id="46647-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="46647-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="46647-103">Change description</span></span>

<span data-ttu-id="46647-104">在 .NET Core 2.2 和舊版中，<xref:System.ComponentModel.InvalidAsynchronousStateException> 類別可在*system.workflow.componentmodel.activity. TypeConverter*元件中找到。</span><span class="sxs-lookup"><span data-stu-id="46647-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="46647-105">從 .NET Core 3.0 開始，它會在*system.workflow.componentmodel.activity*元件中找到。</span><span class="sxs-lookup"><span data-stu-id="46647-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="46647-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="46647-106">Version introduced</span></span>

<span data-ttu-id="46647-107">3.0</span><span class="sxs-lookup"><span data-stu-id="46647-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="46647-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="46647-108">Recommended action</span></span>

<span data-ttu-id="46647-109">這項變更只會影響使用反映的應用程式，藉由呼叫方法（例如 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>）或假設該類型在特定元件中的 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 多載，來載入 <xref:System.ComponentModel.InvalidAsynchronousStateException>。</span><span class="sxs-lookup"><span data-stu-id="46647-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="46647-110">如果是這種情況，則應該更新方法呼叫中所參考元件的元件，以反映類型的新元件位置。</span><span class="sxs-lookup"><span data-stu-id="46647-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="46647-111">Category</span><span class="sxs-lookup"><span data-stu-id="46647-111">Category</span></span>

<span data-ttu-id="46647-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="46647-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="46647-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="46647-113">Affected APIs</span></span>

- <span data-ttu-id="46647-114">None</span><span class="sxs-lookup"><span data-stu-id="46647-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

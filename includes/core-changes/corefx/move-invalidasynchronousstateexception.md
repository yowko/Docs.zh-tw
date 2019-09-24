---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217098"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="a0e71-101">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="a0e71-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="a0e71-102">已<xref:System.ComponentModel.InvalidAsynchronousStateException>移動類別。</span><span class="sxs-lookup"><span data-stu-id="a0e71-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a0e71-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="a0e71-103">Change description</span></span>

<span data-ttu-id="a0e71-104">在 .net Core 2.2 和更早版本中<xref:System.ComponentModel.InvalidAsynchronousStateException> ，類別位於*system.workflow.componentmodel.activity*中。</span><span class="sxs-lookup"><span data-stu-id="a0e71-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="a0e71-105">從 .NET Core 3.0 開始，它會在*system.workflow.componentmodel.activity*元件中找到。</span><span class="sxs-lookup"><span data-stu-id="a0e71-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a0e71-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a0e71-106">Version introduced</span></span>

<span data-ttu-id="a0e71-107">3.0</span><span class="sxs-lookup"><span data-stu-id="a0e71-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a0e71-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a0e71-108">Recommended action</span></span>

<span data-ttu-id="a0e71-109">這項變更只會影響使用反映的應用程式<xref:System.ComponentModel.InvalidAsynchronousStateException>來載入，其方式是<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>呼叫方法（例如<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> ）或的多載，其假設該類型是在特定元件中。</span><span class="sxs-lookup"><span data-stu-id="a0e71-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="a0e71-110">如果是這種情況，則應該更新方法呼叫中所參考元件的元件，以反映類型的新元件位置。</span><span class="sxs-lookup"><span data-stu-id="a0e71-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="a0e71-111">分類</span><span class="sxs-lookup"><span data-stu-id="a0e71-111">Category</span></span>

<span data-ttu-id="a0e71-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="a0e71-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a0e71-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a0e71-113">Affected APIs</span></span>

- <span data-ttu-id="a0e71-114">None</span><span class="sxs-lookup"><span data-stu-id="a0e71-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

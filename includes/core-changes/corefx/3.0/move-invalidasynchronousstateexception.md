---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158464"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="b34a9-101">System.componentmodel.invalidasynchronousstateexception 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="b34a9-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="b34a9-102">已<xref:System.ComponentModel.InvalidAsynchronousStateException>移動類別。</span><span class="sxs-lookup"><span data-stu-id="b34a9-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b34a9-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="b34a9-103">Change description</span></span>

<span data-ttu-id="b34a9-104">在 .NET Core 2.2 和更早版本中<xref:System.ComponentModel.InvalidAsynchronousStateException> ，類別位於*system.workflow.componentmodel.activity*中。</span><span class="sxs-lookup"><span data-stu-id="b34a9-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="b34a9-105">從 .NET Core 3.0 開始，它會在*system.workflow.componentmodel.activity*元件中找到。</span><span class="sxs-lookup"><span data-stu-id="b34a9-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b34a9-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b34a9-106">Version introduced</span></span>

<span data-ttu-id="b34a9-107">3.0</span><span class="sxs-lookup"><span data-stu-id="b34a9-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b34a9-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b34a9-108">Recommended action</span></span>

<span data-ttu-id="b34a9-109">這項變更只會影響使用反映的應用程式<xref:System.ComponentModel.InvalidAsynchronousStateException>來載入，其方式是<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>呼叫方法（例如<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> ）或的多載，其假設該類型是在特定元件中。</span><span class="sxs-lookup"><span data-stu-id="b34a9-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="b34a9-110">如果是這種情況，請更新方法呼叫中所參考的元件，以反映類型的新元件位置。</span><span class="sxs-lookup"><span data-stu-id="b34a9-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="b34a9-111">類別</span><span class="sxs-lookup"><span data-stu-id="b34a9-111">Category</span></span>

<span data-ttu-id="b34a9-112">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="b34a9-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b34a9-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b34a9-113">Affected APIs</span></span>

<span data-ttu-id="b34a9-114">無。</span><span class="sxs-lookup"><span data-stu-id="b34a9-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

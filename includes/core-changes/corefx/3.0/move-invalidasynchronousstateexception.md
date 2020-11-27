---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032025"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="5eeed-101">System.componentmodel.invalidasynchronousstateexception 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="5eeed-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="5eeed-102">已 <xref:System.ComponentModel.InvalidAsynchronousStateException> 移動類別。</span><span class="sxs-lookup"><span data-stu-id="5eeed-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5eeed-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="5eeed-103">Change description</span></span>

<span data-ttu-id="5eeed-104">在 .NET Core 2.2 和較早的版本中， <xref:System.ComponentModel.InvalidAsynchronousStateException> 會在 *ComponentModel* 元件中找到類別。</span><span class="sxs-lookup"><span data-stu-id="5eeed-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="5eeed-105">從 .NET Core 3.0 開始，它會在 *ComponentModel* 元件中找到。</span><span class="sxs-lookup"><span data-stu-id="5eeed-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5eeed-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5eeed-106">Version introduced</span></span>

<span data-ttu-id="5eeed-107">3.0</span><span class="sxs-lookup"><span data-stu-id="5eeed-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5eeed-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5eeed-108">Recommended action</span></span>

<span data-ttu-id="5eeed-109">這項變更只會影響使用反映來載入的應用程式， <xref:System.ComponentModel.InvalidAsynchronousStateException> 方法是呼叫方法（例如）或的多載（ <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 其會假設該型別在特定元件中）。</span><span class="sxs-lookup"><span data-stu-id="5eeed-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="5eeed-110">如果是這種情況，請更新方法呼叫中參考的元件，以反映類型的新元件位置。</span><span class="sxs-lookup"><span data-stu-id="5eeed-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="5eeed-111">類別</span><span class="sxs-lookup"><span data-stu-id="5eeed-111">Category</span></span>

<span data-ttu-id="5eeed-112">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="5eeed-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5eeed-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5eeed-113">Affected APIs</span></span>

<span data-ttu-id="5eeed-114">無。</span><span class="sxs-lookup"><span data-stu-id="5eeed-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->

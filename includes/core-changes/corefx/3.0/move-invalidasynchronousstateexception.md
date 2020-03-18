---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147545"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="ea41f-101">不正確非同步狀態異常移動到另一個程式集</span><span class="sxs-lookup"><span data-stu-id="ea41f-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="ea41f-102">類<xref:System.ComponentModel.InvalidAsynchronousStateException>已移動。</span><span class="sxs-lookup"><span data-stu-id="ea41f-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ea41f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ea41f-103">Change description</span></span>

<span data-ttu-id="ea41f-104">在 .NET Core 2.2 和<xref:System.ComponentModel.InvalidAsynchronousStateException>早期版本中，類位於*System.元件模型.TypeConverter*程式集中。</span><span class="sxs-lookup"><span data-stu-id="ea41f-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="ea41f-105">從 .NET Core 3.0 開始，它位於*系統.元件模型.原始程式集中*。</span><span class="sxs-lookup"><span data-stu-id="ea41f-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ea41f-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="ea41f-106">Version introduced</span></span>

<span data-ttu-id="ea41f-107">3.0</span><span class="sxs-lookup"><span data-stu-id="ea41f-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ea41f-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ea41f-108">Recommended action</span></span>

<span data-ttu-id="ea41f-109">此更改僅影響使用反射來載入 的應用程式<xref:System.ComponentModel.InvalidAsynchronousStateException>，方法是調用 方法，如<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>或 重<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>載，假定類型位於特定程式集中。</span><span class="sxs-lookup"><span data-stu-id="ea41f-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="ea41f-110">如果是這種情況，則應更新方法調用中引用的程式集以反映類型的新程式集位置。</span><span class="sxs-lookup"><span data-stu-id="ea41f-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="ea41f-111">類別</span><span class="sxs-lookup"><span data-stu-id="ea41f-111">Category</span></span>

<span data-ttu-id="ea41f-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ea41f-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ea41f-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ea41f-113">Affected APIs</span></span>

<span data-ttu-id="ea41f-114">無。</span><span class="sxs-lookup"><span data-stu-id="ea41f-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021637"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="8864f-101">不合法的異步狀態異常移至另一個程式集</span><span class="sxs-lookup"><span data-stu-id="8864f-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="8864f-102">類<xref:System.ComponentModel.InvalidAsynchronousStateException>已移動。</span><span class="sxs-lookup"><span data-stu-id="8864f-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8864f-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="8864f-103">Change description</span></span>

<span data-ttu-id="8864f-104">在 .NET Core 2.2 和<xref:System.ComponentModel.InvalidAsynchronousStateException>早期版本中,類位於*System.元件模型.TypeConverter*程式集中。</span><span class="sxs-lookup"><span data-stu-id="8864f-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="8864f-105">從 .NET Core 3.0 開始,它位於*系統.元件模型.原始程式集中*。</span><span class="sxs-lookup"><span data-stu-id="8864f-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8864f-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8864f-106">Version introduced</span></span>

<span data-ttu-id="8864f-107">3.0</span><span class="sxs-lookup"><span data-stu-id="8864f-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8864f-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="8864f-108">Recommended action</span></span>

<span data-ttu-id="8864f-109">此更改僅影響使用反射來載入 的<xref:System.ComponentModel.InvalidAsynchronousStateException>應用程式 ,方法是調用<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>方法,<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>如或重載,假定類型位於特定程式集中。</span><span class="sxs-lookup"><span data-stu-id="8864f-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="8864f-110">如果是這種情況,則應更新方法調用中引用的程式集以反映類型的新程式集位置。</span><span class="sxs-lookup"><span data-stu-id="8864f-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="8864f-111">類別</span><span class="sxs-lookup"><span data-stu-id="8864f-111">Category</span></span>

<span data-ttu-id="8864f-112">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="8864f-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8864f-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8864f-113">Affected APIs</span></span>

<span data-ttu-id="8864f-114">無。</span><span class="sxs-lookup"><span data-stu-id="8864f-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

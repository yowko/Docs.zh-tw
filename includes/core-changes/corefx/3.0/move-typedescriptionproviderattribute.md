---
ms.openlocfilehash: 7a2617f27dfd6bb527ff6d408fae6382075f24ae
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032031"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="33d72-101">TypeDescriptionProviderAttribute 移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="33d72-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="33d72-102">已 <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 移動類別。</span><span class="sxs-lookup"><span data-stu-id="33d72-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="33d72-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="33d72-103">Change description</span></span>

<span data-ttu-id="33d72-104">在 .NET Core 2.2 和較早的版本中， <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 會在 *ComponentModel* 元件中找到類別。</span><span class="sxs-lookup"><span data-stu-id="33d72-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="33d72-105">從 .NET Core 3.0 開始，它會在 *system.collections.objectmodel.observablecollection* 元件中找到。</span><span class="sxs-lookup"><span data-stu-id="33d72-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="33d72-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="33d72-106">Version introduced</span></span>

<span data-ttu-id="33d72-107">3.0</span><span class="sxs-lookup"><span data-stu-id="33d72-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="33d72-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="33d72-108">Recommended action</span></span>

<span data-ttu-id="33d72-109">這項變更只會影響使用反映來載入類型的應用程式， <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 方法是呼叫方法（例如）或的多載（ <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 其會假設類型在特定元件中）。</span><span class="sxs-lookup"><span data-stu-id="33d72-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="33d72-110">如果是這種情況，則應該更新方法呼叫中所參考的元件，以反映類型的新元件位置。</span><span class="sxs-lookup"><span data-stu-id="33d72-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="33d72-111">類別</span><span class="sxs-lookup"><span data-stu-id="33d72-111">Category</span></span>

<span data-ttu-id="33d72-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33d72-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="33d72-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="33d72-113">Affected APIs</span></span>

<span data-ttu-id="33d72-114">無。</span><span class="sxs-lookup"><span data-stu-id="33d72-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->

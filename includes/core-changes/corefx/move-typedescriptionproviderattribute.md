---
ms.openlocfilehash: 4fbec1028b6d75b90d4638814c877c263c8c8936
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182008"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="9dd71-101">TypeDescriptionProviderAttribute 已移至另一個元件</span><span class="sxs-lookup"><span data-stu-id="9dd71-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="9dd71-102">已<xref:System.ComponentModel.TypeDescriptionProviderAttribute>移動類別。</span><span class="sxs-lookup"><span data-stu-id="9dd71-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9dd71-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="9dd71-103">Change description</span></span>

<span data-ttu-id="9dd71-104">在 .net Core 2.2 和更早版本中<xref:System.ComponentModel.TypeDescriptionProviderAttribute> ，類別位於*system.workflow.componentmodel.activity*中。</span><span class="sxs-lookup"><span data-stu-id="9dd71-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="9dd71-105">從 .NET Core 3.0 開始，它會在*system.collections.objectmodel.observablecollection*元件中找到。</span><span class="sxs-lookup"><span data-stu-id="9dd71-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9dd71-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9dd71-106">Version introduced</span></span>

<span data-ttu-id="9dd71-107">3.0</span><span class="sxs-lookup"><span data-stu-id="9dd71-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9dd71-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9dd71-108">Recommended action</span></span>

<span data-ttu-id="9dd71-109">這項變更只會影響使用反映的應用程式<xref:System.ComponentModel.TypeDescriptionProviderAttribute> ，藉由呼叫方法（例如<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ）或<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>的多載（假設該類型是在特定元件中）來載入類型。</span><span class="sxs-lookup"><span data-stu-id="9dd71-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="9dd71-110">如果是這種情況，則應該更新方法呼叫中所參考的元件，以反映類型的新元件位置。</span><span class="sxs-lookup"><span data-stu-id="9dd71-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="9dd71-111">分類</span><span class="sxs-lookup"><span data-stu-id="9dd71-111">Category</span></span>

<span data-ttu-id="9dd71-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9dd71-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9dd71-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9dd71-113">Affected APIs</span></span>

- <span data-ttu-id="9dd71-114">None</span><span class="sxs-lookup"><span data-stu-id="9dd71-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
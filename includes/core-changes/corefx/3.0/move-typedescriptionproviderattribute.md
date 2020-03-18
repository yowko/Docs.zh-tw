---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147532"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="cded0-101">類型描述提供程式屬性移動到另一個程式集</span><span class="sxs-lookup"><span data-stu-id="cded0-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="cded0-102">類<xref:System.ComponentModel.TypeDescriptionProviderAttribute>已移動。</span><span class="sxs-lookup"><span data-stu-id="cded0-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cded0-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="cded0-103">Change description</span></span>

<span data-ttu-id="cded0-104">在 .NET Core 2.2 和<xref:System.ComponentModel.TypeDescriptionProviderAttribute>早期版本中，該類位於*System.元件模型.TypeConverter*程式集中。</span><span class="sxs-lookup"><span data-stu-id="cded0-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="cded0-105">從 .NET Core 3.0 開始，它位於*System.ObjectModel*程式集中。</span><span class="sxs-lookup"><span data-stu-id="cded0-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cded0-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="cded0-106">Version introduced</span></span>

<span data-ttu-id="cded0-107">3.0</span><span class="sxs-lookup"><span data-stu-id="cded0-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cded0-108">建議的動作</span><span class="sxs-lookup"><span data-stu-id="cded0-108">Recommended action</span></span>

<span data-ttu-id="cded0-109">此更改僅影響使用反射來載入<xref:System.ComponentModel.TypeDescriptionProviderAttribute>類型的應用程式，方法是調用方法（如 或<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>重載<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>，假定類型位於特定程式集中）。</span><span class="sxs-lookup"><span data-stu-id="cded0-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="cded0-110">如果是這種情況，則應更新方法調用中引用的程式集以反映類型的新程式集位置。</span><span class="sxs-lookup"><span data-stu-id="cded0-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="cded0-111">類別</span><span class="sxs-lookup"><span data-stu-id="cded0-111">Category</span></span>

<span data-ttu-id="cded0-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cded0-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cded0-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="cded0-113">Affected APIs</span></span>

<span data-ttu-id="cded0-114">無。</span><span class="sxs-lookup"><span data-stu-id="cded0-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

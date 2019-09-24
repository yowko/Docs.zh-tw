---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217042"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="428b0-101">已從某些 Windows Forms 類型中移除 SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="428b0-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="428b0-102"><xref:System.SerializableAttribute>已從某些沒有已知二進位序列化案例的 Windows Forms 類別中移除。</span><span class="sxs-lookup"><span data-stu-id="428b0-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="428b0-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="428b0-103">Change description</span></span>

<span data-ttu-id="428b0-104">下列型別會使用中的<xref:System.SerializableAttribute>來裝飾 .NET Framework 中的，但已移除 .net Core 中的屬性：</span><span class="sxs-lookup"><span data-stu-id="428b0-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="428b0-105">在過去，這個序列化機制已經有嚴重的維護和安全性考慮。</span><span class="sxs-lookup"><span data-stu-id="428b0-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="428b0-106">維護`SerializableAttribute`類型表示這些類型必須經過測試，才能進行版本對版本的序列化變更，以及可能的架構對架構序列化變更。</span><span class="sxs-lookup"><span data-stu-id="428b0-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="428b0-107">這會讓您更難演變這些類型，而且維護成本可能會很高。</span><span class="sxs-lookup"><span data-stu-id="428b0-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="428b0-108">這些類型沒有已知的二進位序列化案例，可將移除屬性的影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="428b0-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="428b0-109">如需詳細資訊，請參閱[二進位序列化](~/docs/standard/serialization/binary-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="428b0-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="428b0-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="428b0-110">Version introduced</span></span>

<span data-ttu-id="428b0-111">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="428b0-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="428b0-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="428b0-112">Recommended action</span></span>

<span data-ttu-id="428b0-113">更新可能相依于標記為 serializable 之這些類型的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="428b0-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="428b0-114">分類</span><span class="sxs-lookup"><span data-stu-id="428b0-114">Category</span></span>

<span data-ttu-id="428b0-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="428b0-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="428b0-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="428b0-116">Affected APIs</span></span>

- <span data-ttu-id="428b0-117">None</span><span class="sxs-lookup"><span data-stu-id="428b0-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

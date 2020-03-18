---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643953"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="5e2a8-101">從某些 Windows 表單類型中刪除的可序列化屬性</span><span class="sxs-lookup"><span data-stu-id="5e2a8-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="5e2a8-102"><xref:System.SerializableAttribute>已從某些沒有已知二進位序列化方案的 Windows 表單類中刪除。</span><span class="sxs-lookup"><span data-stu-id="5e2a8-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5e2a8-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="5e2a8-103">Change description</span></span>

<span data-ttu-id="5e2a8-104">以下類型使用<xref:System.SerializableAttribute>in .NET 框架進行修飾，但在 .NET Core 中刪除了該屬性：</span><span class="sxs-lookup"><span data-stu-id="5e2a8-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

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

<span data-ttu-id="5e2a8-105">從歷史上看，這種序列化機制一直有著嚴重的維護和安全問題。</span><span class="sxs-lookup"><span data-stu-id="5e2a8-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="5e2a8-106">保持`SerializableAttribute`類型意味著必須測試這些類型的版本到版本序列化更改和潛在的框架到框架序列化更改。</span><span class="sxs-lookup"><span data-stu-id="5e2a8-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="5e2a8-107">這使得發展這些類型變得更加困難，而且維護成本可能很高。</span><span class="sxs-lookup"><span data-stu-id="5e2a8-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="5e2a8-108">這些類型沒有已知的二進位序列化方案，這最大限度地減少了刪除屬性的影響。</span><span class="sxs-lookup"><span data-stu-id="5e2a8-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="5e2a8-109">有關詳細資訊，請參閱[二進位序列化](~/docs/standard/serialization/binary-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="5e2a8-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5e2a8-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="5e2a8-110">Version introduced</span></span>

<span data-ttu-id="5e2a8-111">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="5e2a8-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5e2a8-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5e2a8-112">Recommended action</span></span>

<span data-ttu-id="5e2a8-113">更新可能依賴于標記為可序列化的任何代碼。</span><span class="sxs-lookup"><span data-stu-id="5e2a8-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="5e2a8-114">類別</span><span class="sxs-lookup"><span data-stu-id="5e2a8-114">Category</span></span>

<span data-ttu-id="5e2a8-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e2a8-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5e2a8-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5e2a8-116">Affected APIs</span></span>

- <span data-ttu-id="5e2a8-117">None</span><span class="sxs-lookup"><span data-stu-id="5e2a8-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

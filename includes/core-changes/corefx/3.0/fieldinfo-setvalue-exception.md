---
ms.openlocfilehash: 9f8a790718fbb9d685bb8959808338dc1766bf2c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021616"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="58218-101">欄位資訊.SetValue 引發靜態、僅 it 欄位的異常</span><span class="sxs-lookup"><span data-stu-id="58218-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="58218-102">從 .NET Core 3.0 開始,當您<xref:System.Reflection.FieldAttributes.InitOnly><xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>嘗試通過調用 在靜態欄位上設置值時,將引發異常。</span><span class="sxs-lookup"><span data-stu-id="58218-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="58218-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="58218-103">Change description</span></span>

<span data-ttu-id="58218-104">在 .NET 框架和 .NET Core 版本之前為 3.0,可以通過調用<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>來設置靜態欄位的值,該靜態欄位在初始化後為常量(在[C# 中唯讀](~/docs/csharp/language-reference/keywords/readonly.md))。</span><span class="sxs-lookup"><span data-stu-id="58218-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="58218-105">但是,以這種方式設置這樣的欄位會導致基於目標框架和優化設置的不可預知行為。</span><span class="sxs-lookup"><span data-stu-id="58218-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="58218-106">在 .NET Core 3.0<xref:System.Reflection.FieldInfo.SetValue%2A>和更高版本中 ,當<xref:System.Reflection.FieldAttributes.InitOnly>您調用靜<xref:System.FieldAccessException?displayProperty=nameWithType>態 欄位時, 將引發異常。</span><span class="sxs-lookup"><span data-stu-id="58218-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="58218-107">欄位<xref:System.Reflection.FieldAttributes.InitOnly>是只能在聲明欄位時或在包含類的構造函數中設置的欄位。</span><span class="sxs-lookup"><span data-stu-id="58218-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="58218-108">換句話說,它是在初始化后不變的。</span><span class="sxs-lookup"><span data-stu-id="58218-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="58218-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="58218-109">Version introduced</span></span>

<span data-ttu-id="58218-110">3.0</span><span class="sxs-lookup"><span data-stu-id="58218-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="58218-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="58218-111">Recommended action</span></span>

<span data-ttu-id="58218-112">初始化靜態構造<xref:System.Reflection.FieldAttributes.InitOnly>函數中的靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="58218-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="58218-113">這適用於動態類型和非動態類型。</span><span class="sxs-lookup"><span data-stu-id="58218-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="58218-114">或者,可以從欄位中刪除<xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType>該屬性,然後呼<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>叫 。</span><span class="sxs-lookup"><span data-stu-id="58218-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="58218-115">類別</span><span class="sxs-lookup"><span data-stu-id="58218-115">Category</span></span>

<span data-ttu-id="58218-116">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="58218-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="58218-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="58218-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->

---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032019"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="f794a-101">FieldInfo 會針對靜態、僅限初始欄位擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="f794a-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="f794a-102">從 .NET Core 3.0 開始，當您嘗試透過呼叫來設定靜態欄位的值時，就會擲回例外狀況 <xref:System.Reflection.FieldAttributes.InitOnly> <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="f794a-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f794a-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="f794a-103">Change description</span></span>

<span data-ttu-id="f794a-104">在3.0 之前的 .NET Core .NET Framework 和版本中，您可以藉由呼叫，設定在 [c #) 中](~/docs/csharp/language-reference/keywords/readonly.md) 初始化的靜態欄位值 (readonly <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="f794a-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="f794a-105">不過，以此方式設定這類欄位，會根據目標 framework 和優化設定產生無法預期的行為。</span><span class="sxs-lookup"><span data-stu-id="f794a-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="f794a-106">在 .NET Core 3.0 和更新版本中，當您在 <xref:System.Reflection.FieldInfo.SetValue%2A> 靜態、欄位上呼叫時，會擲回 <xref:System.Reflection.FieldAttributes.InitOnly> 例外狀況 <xref:System.FieldAccessException?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f794a-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="f794a-107"><xref:System.Reflection.FieldAttributes.InitOnly>欄位是一個欄位，只能在宣告或包含類別的函式中設定時設定。</span><span class="sxs-lookup"><span data-stu-id="f794a-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="f794a-108">換句話說，它會在初始化之後是常數。</span><span class="sxs-lookup"><span data-stu-id="f794a-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f794a-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f794a-109">Version introduced</span></span>

<span data-ttu-id="f794a-110">3.0</span><span class="sxs-lookup"><span data-stu-id="f794a-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f794a-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="f794a-111">Recommended action</span></span>

<span data-ttu-id="f794a-112">初始化靜態函式中的靜態、 <xref:System.Reflection.FieldAttributes.InitOnly> 欄位。</span><span class="sxs-lookup"><span data-stu-id="f794a-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="f794a-113">這同時適用于動態和非動態類型。</span><span class="sxs-lookup"><span data-stu-id="f794a-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="f794a-114">或者，您可以 <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> 從欄位中移除屬性，然後呼叫 <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f794a-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="f794a-115">類別</span><span class="sxs-lookup"><span data-stu-id="f794a-115">Category</span></span>

<span data-ttu-id="f794a-116">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="f794a-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f794a-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f794a-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->

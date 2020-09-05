---
ms.openlocfilehash: f011f6ebe0fa85a59f3e69c93bba9eddc4c1689b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497215"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="8a0a2-101">無法再將反映物件從受控程式碼傳遞至跨處理序的 DCOM 用戶端</span><span class="sxs-lookup"><span data-stu-id="8a0a2-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="8a0a2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8a0a2-102">Details</span></span>

<span data-ttu-id="8a0a2-103">無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="8a0a2-104">以下是受到影響的類型：</span><span class="sxs-lookup"><span data-stu-id="8a0a2-104">The following types are affected:</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <span data-ttu-id="8a0a2-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (和其衍生的類型，包括 <xref:System.Reflection.FieldInfo?displayProperty=fullName>、<xref:System.Reflection.MethodInfo?displayProperty=fullName>、<xref:System.Type?displayProperty=fullName> 和 <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span><span class="sxs-lookup"><span data-stu-id="8a0a2-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>

<span data-ttu-id="8a0a2-106">呼叫物件的 <code>IMarshal</code> 會傳回 <code>E_NOINTERFACE</code>。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-106">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8a0a2-107">建議</span><span class="sxs-lookup"><span data-stu-id="8a0a2-107">Suggestion</span></span>

<span data-ttu-id="8a0a2-108">更新封送處理常式代碼以使用非反映物件。</span><span class="sxs-lookup"><span data-stu-id="8a0a2-108">Update marshaling code to work with non-reflection objects.</span></span>

| <span data-ttu-id="8a0a2-109">名稱</span><span class="sxs-lookup"><span data-stu-id="8a0a2-109">Name</span></span>    | <span data-ttu-id="8a0a2-110">值</span><span class="sxs-lookup"><span data-stu-id="8a0a2-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8a0a2-111">範圍</span><span class="sxs-lookup"><span data-stu-id="8a0a2-111">Scope</span></span>   |<span data-ttu-id="8a0a2-112">Minor</span><span class="sxs-lookup"><span data-stu-id="8a0a2-112">Minor</span></span>|
|<span data-ttu-id="8a0a2-113">版本</span><span class="sxs-lookup"><span data-stu-id="8a0a2-113">Version</span></span>|<span data-ttu-id="8a0a2-114">4.6</span><span class="sxs-lookup"><span data-stu-id="8a0a2-114">4.6</span></span>|
|<span data-ttu-id="8a0a2-115">類型</span><span class="sxs-lookup"><span data-stu-id="8a0a2-115">Type</span></span>|<span data-ttu-id="8a0a2-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="8a0a2-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="8a0a2-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8a0a2-117">Affected APIs</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <xref:System.Reflection.FieldInfo?displayProperty=fullName>
- <xref:System.Reflection.MemberInfo?displayProperty=fullName>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.MethodInfo?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>
- <xref:System.Reflection.TypeInfo?displayProperty=fullName>
- <xref:System.Type?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Reflection.Assembly`
- `T:System.Reflection.FieldInfo`
- `T:System.Reflection.MemberInfo`
- `T:System.Reflection.MethodBody`
- `T:System.Reflection.MethodInfo`
- `T:System.Reflection.Module`
- `T:System.Reflection.ParameterInfo`
- `T:System.Reflection.TypeInfo`
- `T:System.Type`

-->

---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621144"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="24f90-101">無法再將反映物件從受控程式碼傳遞至跨處理序的 DCOM 用戶端</span><span class="sxs-lookup"><span data-stu-id="24f90-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="24f90-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="24f90-102">Details</span></span>

<span data-ttu-id="24f90-103">無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。</span><span class="sxs-lookup"><span data-stu-id="24f90-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="24f90-104">以下是受到影響的類型：</span><span class="sxs-lookup"><span data-stu-id="24f90-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><span data-ttu-id="24f90-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (和其衍生的類型，包括 <xref:System.Reflection.FieldInfo?displayProperty=fullName>、<xref:System.Reflection.MethodInfo?displayProperty=fullName>、<xref:System.Type?displayProperty=fullName> 和 <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span><span class="sxs-lookup"><span data-stu-id="24f90-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><span data-ttu-id="24f90-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="24f90-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span></span></li></ul><span data-ttu-id="24f90-107">呼叫物件的 <code>IMarshal</code> 會傳回 <code>E_NOINTERFACE</code>。</span><span class="sxs-lookup"><span data-stu-id="24f90-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="24f90-108">建議</span><span class="sxs-lookup"><span data-stu-id="24f90-108">Suggestion</span></span>

<span data-ttu-id="24f90-109">請更新封送處理程式碼以搭配非反映物件使用</span><span class="sxs-lookup"><span data-stu-id="24f90-109">Update marshaling code to work with non-reflection objects</span></span>

| <span data-ttu-id="24f90-110">名稱</span><span class="sxs-lookup"><span data-stu-id="24f90-110">Name</span></span>    | <span data-ttu-id="24f90-111">值</span><span class="sxs-lookup"><span data-stu-id="24f90-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="24f90-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="24f90-112">Scope</span></span>   |<span data-ttu-id="24f90-113">Minor</span><span class="sxs-lookup"><span data-stu-id="24f90-113">Minor</span></span>|
|<span data-ttu-id="24f90-114">版本</span><span class="sxs-lookup"><span data-stu-id="24f90-114">Version</span></span>|<span data-ttu-id="24f90-115">4.6</span><span class="sxs-lookup"><span data-stu-id="24f90-115">4.6</span></span>|
|<span data-ttu-id="24f90-116">類型</span><span class="sxs-lookup"><span data-stu-id="24f90-116">Type</span></span>|<span data-ttu-id="24f90-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="24f90-117">Runtime</span></span>|

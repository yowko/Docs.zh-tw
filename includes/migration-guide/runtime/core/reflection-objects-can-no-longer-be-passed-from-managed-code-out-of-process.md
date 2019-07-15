---
ms.openlocfilehash: d00f86c492a7d32344b1067a48c8e53aa2a43426
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858580"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="c3126-101">無法再將反映物件從受控程式碼傳遞至跨處理序的 DCOM 用戶端</span><span class="sxs-lookup"><span data-stu-id="c3126-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

|   |   |
|---|---|
|<span data-ttu-id="c3126-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c3126-102">Details</span></span>|<span data-ttu-id="c3126-103">無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。</span><span class="sxs-lookup"><span data-stu-id="c3126-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="c3126-104">以下是受到影響的類型：</span><span class="sxs-lookup"><span data-stu-id="c3126-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><span data-ttu-id="c3126-105"><xref:System.Reflection.MemberInfo?displayProperty=name> (和其衍生的類型，包括 <xref:System.Reflection.FieldInfo?displayProperty=name>、<xref:System.Reflection.MethodInfo?displayProperty=name>、<xref:System.Type?displayProperty=name> 和 <xref:System.Reflection.TypeInfo?displayProperty=name>)</span><span class="sxs-lookup"><span data-stu-id="c3126-105"><xref:System.Reflection.MemberInfo?displayProperty=name> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, and <xref:System.Reflection.TypeInfo?displayProperty=name>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><span data-ttu-id="c3126-106"><xref:System.Reflection.ParameterInfo?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="c3126-106"><xref:System.Reflection.ParameterInfo?displayProperty=name>.</span></span></li></ul><span data-ttu-id="c3126-107">呼叫物件的 <code>IMarshal</code> 會傳回 <code>E_NOINTERFACE</code>。</span><span class="sxs-lookup"><span data-stu-id="c3126-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>|
|<span data-ttu-id="c3126-108">建議</span><span class="sxs-lookup"><span data-stu-id="c3126-108">Suggestion</span></span>|<span data-ttu-id="c3126-109">請更新封送處理程式碼以搭配非反映物件使用</span><span class="sxs-lookup"><span data-stu-id="c3126-109">Update marshaling code to work with non-reflection objects</span></span>|
|<span data-ttu-id="c3126-110">範圍</span><span class="sxs-lookup"><span data-stu-id="c3126-110">Scope</span></span>|<span data-ttu-id="c3126-111">次要</span><span class="sxs-lookup"><span data-stu-id="c3126-111">Minor</span></span>|
|<span data-ttu-id="c3126-112">版本</span><span class="sxs-lookup"><span data-stu-id="c3126-112">Version</span></span>|<span data-ttu-id="c3126-113">4.6</span><span class="sxs-lookup"><span data-stu-id="c3126-113">4.6</span></span>|
|<span data-ttu-id="c3126-114">類型</span><span class="sxs-lookup"><span data-stu-id="c3126-114">Type</span></span>|<span data-ttu-id="c3126-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="c3126-115">Runtime</span></span>|


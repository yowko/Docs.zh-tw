---
ms.openlocfilehash: 38c774417fc94fa080bf2b82c04d575e9068cdcb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234099"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="8219c-101">無法再將反映物件從受控程式碼傳遞至跨處理序的 DCOM 用戶端</span><span class="sxs-lookup"><span data-stu-id="8219c-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8219c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8219c-102">Details</span></span>|<span data-ttu-id="8219c-103">無法再將反映物件從 Managed 程式碼傳遞至跨處理序的 DCOM 用戶端。</span><span class="sxs-lookup"><span data-stu-id="8219c-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="8219c-104">以下是受到影響的類型：</span><span class="sxs-lookup"><span data-stu-id="8219c-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> <span data-ttu-id="8219c-105">(和其衍生的型別，包括<xref:System.Reflection.FieldInfo?displayProperty=name>、<xref:System.Reflection.MethodInfo?displayProperty=name>、<xref:System.Type?displayProperty=name> 和 <xref:System.Reflection.TypeInfo?displayProperty=name>)</span><span class="sxs-lookup"><span data-stu-id="8219c-105">(and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, and <xref:System.Reflection.TypeInfo?displayProperty=name>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name><span data-ttu-id="8219c-106">。</span><span class="sxs-lookup"><span data-stu-id="8219c-106">.</span></span></li></ul><span data-ttu-id="8219c-107">呼叫物件的 <code>IMarshal</code> 會傳回 <code>E_NOINTERFACE</code>。</span><span class="sxs-lookup"><span data-stu-id="8219c-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>|
|<span data-ttu-id="8219c-108">建議</span><span class="sxs-lookup"><span data-stu-id="8219c-108">Suggestion</span></span>|<span data-ttu-id="8219c-109">請更新封送處理程式碼以搭配非反映物件使用</span><span class="sxs-lookup"><span data-stu-id="8219c-109">Update marshaling code to work with non-reflection objects</span></span>|
|<span data-ttu-id="8219c-110">範圍</span><span class="sxs-lookup"><span data-stu-id="8219c-110">Scope</span></span>|<span data-ttu-id="8219c-111">次要</span><span class="sxs-lookup"><span data-stu-id="8219c-111">Minor</span></span>|
|<span data-ttu-id="8219c-112">版本</span><span class="sxs-lookup"><span data-stu-id="8219c-112">Version</span></span>|<span data-ttu-id="8219c-113">4.6</span><span class="sxs-lookup"><span data-stu-id="8219c-113">4.6</span></span>|
|<span data-ttu-id="8219c-114">類型</span><span class="sxs-lookup"><span data-stu-id="8219c-114">Type</span></span>|<span data-ttu-id="8219c-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="8219c-115">Runtime</span></span>|

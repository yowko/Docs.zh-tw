---
title: ICorDebugProcess6::GetExportStepInfo 方法
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a891e6d65d159875f5607ac33b0668414cb380
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137211"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a><span data-ttu-id="6f5e5-102">ICorDebugProcess6::GetExportStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="6f5e5-102">ICorDebugProcess6::GetExportStepInfo Method</span></span>
<span data-ttu-id="6f5e5-103">提供執行階段匯出函式的相關資訊，以協助逐步執行 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-103">Provides information on runtime exported functions to help step through managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f5e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f5e5-104">Syntax</span></span>  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f5e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f5e5-105">Parameters</span></span>  
 <span data-ttu-id="6f5e5-106">pszExportName</span><span class="sxs-lookup"><span data-stu-id="6f5e5-106">pszExportName</span></span>  
 <span data-ttu-id="6f5e5-107">[in] 執行階段匯出函式寫入 PE 匯出資料表時所使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-107">[in] The name of a runtime export function as written in the PE export table.</span></span>  
  
 <span data-ttu-id="6f5e5-108">invokeKind</span><span class="sxs-lookup"><span data-stu-id="6f5e5-108">invokeKind</span></span>  
 <span data-ttu-id="6f5e5-109">[out]成員指標[CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)列舉，描述如何匯出的函式會叫用 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-109">[out] A pointer to a member of the [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeration that describes how the exported function will invoke managed code.</span></span>  
  
 <span data-ttu-id="6f5e5-110">invokePurpose</span><span class="sxs-lookup"><span data-stu-id="6f5e5-110">invokePurpose</span></span>  
 <span data-ttu-id="6f5e5-111">[out]成員指標[CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)描述匯出函式呼叫 managed 程式碼的原因的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-111">[out] A pointer to a member of the [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeration that describes why the exported function will call managed code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f5e5-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f5e5-112">Return Value</span></span>  
 <span data-ttu-id="6f5e5-113">這個方法會傳回下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-113">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="6f5e5-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f5e5-114">Return value</span></span>|<span data-ttu-id="6f5e5-115">描述</span><span class="sxs-lookup"><span data-stu-id="6f5e5-115">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="6f5e5-116">方法呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-116">The method call was successful.</span></span>|  
|`E_POINTER`|`pInvokeKind` <span data-ttu-id="6f5e5-117">或是`pInvokePurpose`已**null**。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-117">or `pInvokePurpose` is **null**.</span></span>|  
|<span data-ttu-id="6f5e5-118">其他失敗的 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-118">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="6f5e5-119">視需要。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-119">As appropriate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f5e5-120">備註</span><span class="sxs-lookup"><span data-stu-id="6f5e5-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f5e5-121">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f5e5-122">需求</span><span class="sxs-lookup"><span data-stu-id="6f5e5-122">Requirements</span></span>  
 <span data-ttu-id="6f5e5-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f5e5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f5e5-124">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f5e5-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f5e5-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f5e5-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6f5e5-126">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6f5e5-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f5e5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f5e5-127">See also</span></span>

- [<span data-ttu-id="6f5e5-128">ICorDebugProcess6 介面</span><span class="sxs-lookup"><span data-stu-id="6f5e5-128">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="6f5e5-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6f5e5-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

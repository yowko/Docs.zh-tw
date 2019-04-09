---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo 方法
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7c72d0766580f9aa3aa678aacd872b804172a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131426"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="558c3-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="558c3-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="558c3-103">請參閱[DefineAsyncStepInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="558c3-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="558c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="558c3-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="558c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="558c3-105">Parameters</span></span>  
  
|<span data-ttu-id="558c3-106">參數</span><span class="sxs-lookup"><span data-stu-id="558c3-106">Parameter</span></span>|<span data-ttu-id="558c3-107">描述</span><span class="sxs-lookup"><span data-stu-id="558c3-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="558c3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="558c3-108">Return Value</span></span>  
 <span data-ttu-id="558c3-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="558c3-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="558c3-110">需求</span><span class="sxs-lookup"><span data-stu-id="558c3-110">Requirements</span></span>  
 <span data-ttu-id="558c3-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="558c3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="558c3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="558c3-112">See also</span></span>

- [<span data-ttu-id="558c3-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="558c3-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

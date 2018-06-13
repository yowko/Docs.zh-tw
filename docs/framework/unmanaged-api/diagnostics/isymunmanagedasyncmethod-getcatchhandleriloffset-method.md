---
title: ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 527e686eb0c354c3a1ebba36772e30211e995ab2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425349"
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="372e8-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="372e8-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="372e8-103">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="372e8-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="372e8-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="372e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="372e8-105">Parameters</span></span>  
  
|<span data-ttu-id="372e8-106">參數</span><span class="sxs-lookup"><span data-stu-id="372e8-106">Parameter</span></span>|<span data-ttu-id="372e8-107">描述</span><span class="sxs-lookup"><span data-stu-id="372e8-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="372e8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="372e8-108">Return Value</span></span>  
 <span data-ttu-id="372e8-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="372e8-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="372e8-110">需求</span><span class="sxs-lookup"><span data-stu-id="372e8-110">Requirements</span></span>  
 <span data-ttu-id="372e8-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="372e8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372e8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="372e8-112">See Also</span></span>  
 [<span data-ttu-id="372e8-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="372e8-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

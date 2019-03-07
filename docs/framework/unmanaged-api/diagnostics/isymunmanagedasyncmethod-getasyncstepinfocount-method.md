---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount 方法
ms.date: 03/30/2017
ms.assetid: 32a4e084-09b2-4946-a4a7-19a1fed9f7cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31c8dbfc6562e2f5da42586160e2b23911fc2bfb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494632"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfocount-method"></a><span data-ttu-id="a16f8-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="a16f8-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Method</span></span>
<span data-ttu-id="a16f8-103">請參閱[DefineAsyncStepInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a16f8-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a16f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="a16f8-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfoCount(    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a16f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="a16f8-105">Parameters</span></span>  
  
|<span data-ttu-id="a16f8-106">參數</span><span class="sxs-lookup"><span data-stu-id="a16f8-106">Parameter</span></span>|<span data-ttu-id="a16f8-107">描述</span><span class="sxs-lookup"><span data-stu-id="a16f8-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="a16f8-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a16f8-108">Return Value</span></span>  
 <span data-ttu-id="a16f8-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="a16f8-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a16f8-110">需求</span><span class="sxs-lookup"><span data-stu-id="a16f8-110">Requirements</span></span>  
 <span data-ttu-id="a16f8-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a16f8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16f8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a16f8-112">See also</span></span>
- [<span data-ttu-id="a16f8-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="a16f8-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

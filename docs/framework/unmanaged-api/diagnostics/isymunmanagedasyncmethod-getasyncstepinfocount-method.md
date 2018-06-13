---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount 方法
ms.date: 03/30/2017
ms.assetid: 32a4e084-09b2-4946-a4a7-19a1fed9f7cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2904fe91f223b528450684d8de2f70dba48fc792
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425060"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfocount-method"></a><span data-ttu-id="30f00-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount 方法</span><span class="sxs-lookup"><span data-stu-id="30f00-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Method</span></span>
<span data-ttu-id="30f00-103">請參閱[DefineAsyncStepInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="30f00-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f00-104">語法</span><span class="sxs-lookup"><span data-stu-id="30f00-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfoCount(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30f00-105">參數</span><span class="sxs-lookup"><span data-stu-id="30f00-105">Parameters</span></span>  
  
|<span data-ttu-id="30f00-106">參數</span><span class="sxs-lookup"><span data-stu-id="30f00-106">Parameter</span></span>|<span data-ttu-id="30f00-107">描述</span><span class="sxs-lookup"><span data-stu-id="30f00-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="30f00-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="30f00-108">Return Value</span></span>  
 <span data-ttu-id="30f00-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="30f00-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30f00-110">需求</span><span class="sxs-lookup"><span data-stu-id="30f00-110">Requirements</span></span>  
 <span data-ttu-id="30f00-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="30f00-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f00-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30f00-112">See Also</span></span>  
 [<span data-ttu-id="30f00-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="30f00-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

---
title: ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cacf9333379566f80d270b172a1f3411bdc81cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509762"
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="61267-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="61267-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="61267-103">請參閱[DefineCatchHandlerILOffset 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="61267-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61267-104">語法</span><span class="sxs-lookup"><span data-stu-id="61267-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61267-105">參數</span><span class="sxs-lookup"><span data-stu-id="61267-105">Parameters</span></span>  
  
|<span data-ttu-id="61267-106">參數</span><span class="sxs-lookup"><span data-stu-id="61267-106">Parameter</span></span>|<span data-ttu-id="61267-107">描述</span><span class="sxs-lookup"><span data-stu-id="61267-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="61267-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="61267-108">Return Value</span></span>  
 <span data-ttu-id="61267-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="61267-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61267-110">需求</span><span class="sxs-lookup"><span data-stu-id="61267-110">Requirements</span></span>  
 <span data-ttu-id="61267-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61267-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61267-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61267-112">See also</span></span>
- [<span data-ttu-id="61267-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="61267-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

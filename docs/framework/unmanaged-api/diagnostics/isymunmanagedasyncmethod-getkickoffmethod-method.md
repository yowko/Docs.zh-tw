---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84aef2b26e008d1a3c6d95d7ec1e130ab0594a11
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484546"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="11536-102">ISymUnmanagedAsyncMethod::GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="11536-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="11536-103">請參閱[DefineKickoffMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="11536-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11536-104">語法</span><span class="sxs-lookup"><span data-stu-id="11536-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11536-105">參數</span><span class="sxs-lookup"><span data-stu-id="11536-105">Parameters</span></span>  
  
|<span data-ttu-id="11536-106">參數</span><span class="sxs-lookup"><span data-stu-id="11536-106">Parameter</span></span>|<span data-ttu-id="11536-107">描述</span><span class="sxs-lookup"><span data-stu-id="11536-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="11536-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="11536-108">Return Value</span></span>  
 <span data-ttu-id="11536-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="11536-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11536-110">需求</span><span class="sxs-lookup"><span data-stu-id="11536-110">Requirements</span></span>  
 <span data-ttu-id="11536-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="11536-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11536-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11536-112">See also</span></span>
- [<span data-ttu-id="11536-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="11536-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

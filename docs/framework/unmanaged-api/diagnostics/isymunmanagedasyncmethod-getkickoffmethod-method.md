---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2f055dc19bf7f40036283102d8cc4549555b992
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424764"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="6beb3-102">ISymUnmanagedAsyncMethod::GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="6beb3-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="6beb3-103">請參閱[DefineKickoffMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="6beb3-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6beb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="6beb3-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6beb3-105">參數</span><span class="sxs-lookup"><span data-stu-id="6beb3-105">Parameters</span></span>  
  
|<span data-ttu-id="6beb3-106">參數</span><span class="sxs-lookup"><span data-stu-id="6beb3-106">Parameter</span></span>|<span data-ttu-id="6beb3-107">描述</span><span class="sxs-lookup"><span data-stu-id="6beb3-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="6beb3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6beb3-108">Return Value</span></span>  
 <span data-ttu-id="6beb3-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="6beb3-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6beb3-110">需求</span><span class="sxs-lookup"><span data-stu-id="6beb3-110">Requirements</span></span>  
 <span data-ttu-id="6beb3-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6beb3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6beb3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6beb3-112">See Also</span></span>  
 [<span data-ttu-id="6beb3-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="6beb3-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

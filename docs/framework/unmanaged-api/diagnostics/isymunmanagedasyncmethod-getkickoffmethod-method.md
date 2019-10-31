---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: 58daec30b4cbae9cfaab27d4ce76521ba839cf83
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139840"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="d8022-102">ISymUnmanagedAsyncMethod::GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="d8022-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="d8022-103">請參閱[DefineKickoffMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d8022-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8022-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8022-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8022-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8022-105">Parameters</span></span>  
  
|<span data-ttu-id="d8022-106">參數</span><span class="sxs-lookup"><span data-stu-id="d8022-106">Parameter</span></span>|<span data-ttu-id="d8022-107">描述</span><span class="sxs-lookup"><span data-stu-id="d8022-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="d8022-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d8022-108">Return Value</span></span>  
 <span data-ttu-id="d8022-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="d8022-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8022-110">需求</span><span class="sxs-lookup"><span data-stu-id="d8022-110">Requirements</span></span>  
 <span data-ttu-id="d8022-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d8022-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8022-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8022-112">See also</span></span>

- [<span data-ttu-id="d8022-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="d8022-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

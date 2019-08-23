---
title: ICorDebugStaticFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d99e06c1093dbc67e9c1999e4b9ccabd6579340e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962667"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="217db-102">ICorDebugStaticFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="217db-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="217db-103">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="217db-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="217db-104">語法</span><span class="sxs-lookup"><span data-stu-id="217db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="217db-105">參數</span><span class="sxs-lookup"><span data-stu-id="217db-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="217db-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="217db-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="217db-107">備註</span><span class="sxs-lookup"><span data-stu-id="217db-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="217db-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="217db-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="217db-109">需求</span><span class="sxs-lookup"><span data-stu-id="217db-109">Requirements</span></span>  
 <span data-ttu-id="217db-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="217db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="217db-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="217db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="217db-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="217db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="217db-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="217db-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217db-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="217db-114">See also</span></span>

- [<span data-ttu-id="217db-115">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="217db-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="217db-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="217db-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

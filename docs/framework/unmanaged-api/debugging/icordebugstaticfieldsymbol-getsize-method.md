---
title: ICorDebugStaticFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9baa3632b6ede9ce45f34302611710344ed33761
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154319"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="01d1d-102">ICorDebugStaticFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="01d1d-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="01d1d-103">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="01d1d-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01d1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="01d1d-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01d1d-105">參數</span><span class="sxs-lookup"><span data-stu-id="01d1d-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="01d1d-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="01d1d-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01d1d-107">備註</span><span class="sxs-lookup"><span data-stu-id="01d1d-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01d1d-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="01d1d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01d1d-109">需求</span><span class="sxs-lookup"><span data-stu-id="01d1d-109">Requirements</span></span>  
 <span data-ttu-id="01d1d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01d1d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01d1d-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01d1d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01d1d-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01d1d-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="01d1d-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="01d1d-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01d1d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01d1d-114">See also</span></span>

- [<span data-ttu-id="01d1d-115">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="01d1d-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="01d1d-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="01d1d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

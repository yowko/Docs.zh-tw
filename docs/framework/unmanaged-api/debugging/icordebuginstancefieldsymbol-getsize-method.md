---
title: ICorDebugInstanceFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2119b1ce43d5969c8d083e955210c69af69b44
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491434"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="d1d16-102">ICorDebugInstanceFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="d1d16-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="d1d16-103">取得執行個體欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="d1d16-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d16-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1d16-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1d16-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1d16-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="d1d16-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="d1d16-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1d16-107">備註</span><span class="sxs-lookup"><span data-stu-id="d1d16-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1d16-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="d1d16-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d16-109">需求</span><span class="sxs-lookup"><span data-stu-id="d1d16-109">Requirements</span></span>  
 <span data-ttu-id="d1d16-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1d16-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d16-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1d16-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1d16-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1d16-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d16-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d16-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d16-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1d16-114">See also</span></span>
- [<span data-ttu-id="d1d16-115">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="d1d16-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="d1d16-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d1d16-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugInstanceFieldSymbol::GetSize 方法
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04d866888c15585ff5058f870257b317ac888be7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696980"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="09f4d-102">ICorDebugInstanceFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="09f4d-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="09f4d-103">取得執行個體欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="09f4d-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09f4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="09f4d-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09f4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="09f4d-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="09f4d-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="09f4d-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09f4d-107">備註</span><span class="sxs-lookup"><span data-stu-id="09f4d-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09f4d-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="09f4d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09f4d-109">需求</span><span class="sxs-lookup"><span data-stu-id="09f4d-109">Requirements</span></span>  
 <span data-ttu-id="09f4d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09f4d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09f4d-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09f4d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09f4d-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09f4d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09f4d-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09f4d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09f4d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09f4d-114">See also</span></span>
- [<span data-ttu-id="09f4d-115">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="09f4d-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="09f4d-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="09f4d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

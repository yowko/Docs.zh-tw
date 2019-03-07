---
title: ICorDebugSymbolProvider::GetCodeRange 方法
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392f526df53474dd2926e631e24ec5449bd1b199
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498467"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="7c122-102">ICorDebugSymbolProvider::GetCodeRange 方法</span><span class="sxs-lookup"><span data-stu-id="7c122-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="7c122-103">提供方法中的相對虛擬位址 (RVA)，以取得方法起始位址和大小。</span><span class="sxs-lookup"><span data-stu-id="7c122-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c122-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c122-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c122-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c122-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="7c122-106">[in] 方法中的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="7c122-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="7c122-107">[out] 方法的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="7c122-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="7c122-108">方法程式碼大小的指標 (方法的程式碼位元組數)。</span><span class="sxs-lookup"><span data-stu-id="7c122-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c122-109">備註</span><span class="sxs-lookup"><span data-stu-id="7c122-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c122-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="7c122-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c122-111">需求</span><span class="sxs-lookup"><span data-stu-id="7c122-111">Requirements</span></span>  
 <span data-ttu-id="7c122-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c122-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c122-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c122-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c122-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c122-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c122-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c122-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c122-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c122-116">See also</span></span>
- [<span data-ttu-id="7c122-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="7c122-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="7c122-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7c122-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

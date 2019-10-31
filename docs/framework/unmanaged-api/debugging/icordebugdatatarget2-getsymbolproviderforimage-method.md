---
title: ICorDebugDataTarget2::GetSymbolProviderForImage 方法
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 64a35f65bc3c31e091e2d94260efb84f20abb795
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122112"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="77a91-102">ICorDebugDataTarget2::GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="77a91-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="77a91-103">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="77a91-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a91-104">語法</span><span class="sxs-lookup"><span data-stu-id="77a91-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77a91-105">參數</span><span class="sxs-lookup"><span data-stu-id="77a91-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="77a91-106">在代表模組基底位址的[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值。</span><span class="sxs-lookup"><span data-stu-id="77a91-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="77a91-107">脫銷[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="77a91-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77a91-108">備註</span><span class="sxs-lookup"><span data-stu-id="77a91-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77a91-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="77a91-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a91-110">需求</span><span class="sxs-lookup"><span data-stu-id="77a91-110">Requirements</span></span>  
 <span data-ttu-id="77a91-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77a91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77a91-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77a91-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77a91-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77a91-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77a91-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77a91-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a91-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="77a91-115">See also</span></span>

- [<span data-ttu-id="77a91-116">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="77a91-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="77a91-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="77a91-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

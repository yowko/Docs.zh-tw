---
title: ICorDebugDataTarget2::GetSymbolProviderForImage 方法
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e5a6e70d5148756a5ed8d17c56577da920d1b69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911455"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="a2162-102">ICorDebugDataTarget2::GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="a2162-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="a2162-103">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="a2162-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2162-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2162-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2162-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2162-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="a2162-106">在代表模組基底位址的[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值。</span><span class="sxs-lookup"><span data-stu-id="a2162-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="a2162-107">脫銷[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="a2162-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2162-108">備註</span><span class="sxs-lookup"><span data-stu-id="a2162-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2162-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="a2162-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2162-110">需求</span><span class="sxs-lookup"><span data-stu-id="a2162-110">Requirements</span></span>  
 <span data-ttu-id="a2162-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2162-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2162-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2162-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2162-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2162-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2162-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2162-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2162-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2162-115">See also</span></span>

- [<span data-ttu-id="a2162-116">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="a2162-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="a2162-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a2162-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

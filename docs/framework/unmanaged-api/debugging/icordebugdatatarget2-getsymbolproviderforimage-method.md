---
title: ICorDebugDataTarget2::GetSymbolProviderForImage 方法
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cdd2d0b6f6fbc8d3c2b1a14ca05a84d13c56331
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411099"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="a1800-102">ICorDebugDataTarget2::GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="a1800-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="a1800-103">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="a1800-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1800-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1800-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1800-105">參數</span><span class="sxs-lookup"><span data-stu-id="a1800-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="a1800-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="a1800-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="a1800-107">[out]位址指標[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="a1800-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1800-108">備註</span><span class="sxs-lookup"><span data-stu-id="a1800-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1800-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="a1800-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1800-110">需求</span><span class="sxs-lookup"><span data-stu-id="a1800-110">Requirements</span></span>  
 <span data-ttu-id="a1800-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1800-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1800-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1800-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1800-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1800-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1800-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1800-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1800-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1800-115">See Also</span></span>  
 [<span data-ttu-id="a1800-116">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="a1800-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="a1800-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a1800-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

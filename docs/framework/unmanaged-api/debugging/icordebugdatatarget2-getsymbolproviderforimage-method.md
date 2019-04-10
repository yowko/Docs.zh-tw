---
title: ICorDebugDataTarget2::GetSymbolProviderForImage 方法
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cda49084c9453f79727f7f57ef152577cb4d7c5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171960"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="49d5a-102">ICorDebugDataTarget2::GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="49d5a-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="49d5a-103">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="49d5a-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="49d5a-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49d5a-105">參數</span><span class="sxs-lookup"><span data-stu-id="49d5a-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="49d5a-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="49d5a-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="49d5a-107">[out]位址指標[ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="49d5a-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49d5a-108">備註</span><span class="sxs-lookup"><span data-stu-id="49d5a-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49d5a-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="49d5a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d5a-110">需求</span><span class="sxs-lookup"><span data-stu-id="49d5a-110">Requirements</span></span>  
 <span data-ttu-id="49d5a-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49d5a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d5a-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49d5a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49d5a-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49d5a-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="49d5a-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="49d5a-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="49d5a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49d5a-115">See also</span></span>

- [<span data-ttu-id="49d5a-116">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="49d5a-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="49d5a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="49d5a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

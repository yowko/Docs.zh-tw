---
title: ICorDebugDataTarget2::GetSymbolProviderForImage 方法
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: bada60295c3a9b3a702aa674e06f8f5cf6ac0a24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788832"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="a5c8d-102">ICorDebugDataTarget2::GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="a5c8d-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="a5c8d-103">從模組的基底位址傳回模組的符號提供者。</span><span class="sxs-lookup"><span data-stu-id="a5c8d-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5c8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5c8d-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="a5c8d-106">在[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="a5c8d-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="a5c8d-107">脫銷[ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="a5c8d-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c8d-108">備註</span><span class="sxs-lookup"><span data-stu-id="a5c8d-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5c8d-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="a5c8d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c8d-110">需求</span><span class="sxs-lookup"><span data-stu-id="a5c8d-110">Requirements</span></span>  
 <span data-ttu-id="a5c8d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5c8d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c8d-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5c8d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5c8d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5c8d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5c8d-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5c8d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c8d-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5c8d-115">See also</span></span>

- [<span data-ttu-id="a5c8d-116">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="a5c8d-116">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="a5c8d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a5c8d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

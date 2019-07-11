---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d96aa82e9fd8b651ab005cba4945f6977c1e3d3a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771498"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="f3b4e-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="f3b4e-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="f3b4e-103">從合併組件傳回中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f3b4e-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3b4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3b4e-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3b4e-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="f3b4e-106">[out]位址指標[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)包含大小和合併組件的中繼資料位址的相關資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="f3b4e-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3b4e-107">備註</span><span class="sxs-lookup"><span data-stu-id="f3b4e-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3b4e-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="f3b4e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3b4e-109">需求</span><span class="sxs-lookup"><span data-stu-id="f3b4e-109">Requirements</span></span>  
 <span data-ttu-id="f3b4e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3b4e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3b4e-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3b4e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3b4e-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3b4e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3b4e-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3b4e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b4e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3b4e-114">See also</span></span>

- [<span data-ttu-id="f3b4e-115">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="f3b4e-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f3b4e-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f3b4e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

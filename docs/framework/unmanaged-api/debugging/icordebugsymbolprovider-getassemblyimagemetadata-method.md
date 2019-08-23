---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad86c42d0f23de25fe0e5b9123a0dba3695d8d64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964650"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="8a86f-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="8a86f-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="8a86f-103">從合併組件傳回中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8a86f-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a86f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a86f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a86f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a86f-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="8a86f-106">脫銷[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)物件位址的指標, 其中包含合併元件中繼資料之大小和位址的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8a86f-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a86f-107">備註</span><span class="sxs-lookup"><span data-stu-id="8a86f-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a86f-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8a86f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a86f-109">需求</span><span class="sxs-lookup"><span data-stu-id="8a86f-109">Requirements</span></span>  
 <span data-ttu-id="8a86f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a86f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a86f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a86f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a86f-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a86f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a86f-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a86f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a86f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a86f-114">See also</span></span>

- [<span data-ttu-id="8a86f-115">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="8a86f-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8a86f-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8a86f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

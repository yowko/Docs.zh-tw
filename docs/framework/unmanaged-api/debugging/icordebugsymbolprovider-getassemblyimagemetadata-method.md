---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cb255330937b00a987ee0d07f0332d04fe1746d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489975"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="9e036-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="9e036-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="9e036-103">從合併組件傳回中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9e036-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e036-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e036-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e036-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e036-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="9e036-106">[out]位址指標[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)包含大小和合併組件的中繼資料位址的相關資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="9e036-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e036-107">備註</span><span class="sxs-lookup"><span data-stu-id="9e036-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e036-108">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="9e036-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e036-109">需求</span><span class="sxs-lookup"><span data-stu-id="9e036-109">Requirements</span></span>  
 <span data-ttu-id="9e036-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e036-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e036-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e036-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e036-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e036-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e036-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e036-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e036-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e036-114">See also</span></span>
- [<span data-ttu-id="9e036-115">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="9e036-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9e036-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9e036-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: "ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48e5e9daf191cb2f4112dd2a957f29c0a7521398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="fc0db-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="fc0db-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="fc0db-103">從合併組件傳回中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fc0db-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0db-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc0db-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc0db-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc0db-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="fc0db-106">[out]位址指標[ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)物件，其中包含大小和合併的組件中繼資料位址的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fc0db-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc0db-107">備註</span><span class="sxs-lookup"><span data-stu-id="fc0db-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc0db-108">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="fc0db-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0db-109">需求</span><span class="sxs-lookup"><span data-stu-id="fc0db-109">Requirements</span></span>  
 <span data-ttu-id="fc0db-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc0db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc0db-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc0db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc0db-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc0db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc0db-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc0db-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0db-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc0db-114">See Also</span></span>  
 [<span data-ttu-id="fc0db-115">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="fc0db-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="fc0db-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fc0db-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

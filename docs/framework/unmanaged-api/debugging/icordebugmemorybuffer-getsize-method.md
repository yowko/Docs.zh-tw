---
title: "ICorDebugMemoryBuffer::GetSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a21198c70512af703e106870d1bc3f7882d62fe9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="b7e40-102">ICorDebugMemoryBuffer::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="b7e40-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="b7e40-103">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="b7e40-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7e40-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7e40-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7e40-105">參數</span><span class="sxs-lookup"><span data-stu-id="b7e40-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="b7e40-106">[out] 記憶體緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="b7e40-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7e40-107">備註</span><span class="sxs-lookup"><span data-stu-id="b7e40-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7e40-108">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="b7e40-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7e40-109">需求</span><span class="sxs-lookup"><span data-stu-id="b7e40-109">Requirements</span></span>  
 <span data-ttu-id="b7e40-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7e40-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7e40-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7e40-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7e40-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7e40-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7e40-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7e40-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7e40-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7e40-114">See Also</span></span>  
 [<span data-ttu-id="b7e40-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="b7e40-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="b7e40-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b7e40-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

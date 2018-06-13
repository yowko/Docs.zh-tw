---
title: ICorDebugMemoryBuffer::GetSize 方法
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caf95e0b5c8d4ae942bb428f53d4e58313e0e78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414748"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="51348-102">ICorDebugMemoryBuffer::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="51348-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="51348-103">取得以位元組為單位的記憶體緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="51348-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51348-104">語法</span><span class="sxs-lookup"><span data-stu-id="51348-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51348-105">參數</span><span class="sxs-lookup"><span data-stu-id="51348-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="51348-106">[out] 記憶體緩衝區大小的指標。</span><span class="sxs-lookup"><span data-stu-id="51348-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51348-107">備註</span><span class="sxs-lookup"><span data-stu-id="51348-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51348-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="51348-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51348-109">需求</span><span class="sxs-lookup"><span data-stu-id="51348-109">Requirements</span></span>  
 <span data-ttu-id="51348-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51348-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51348-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51348-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51348-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51348-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51348-113">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51348-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51348-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51348-114">See Also</span></span>  
 [<span data-ttu-id="51348-115">ICorDebugMemoryBuffer 介面</span><span class="sxs-lookup"><span data-stu-id="51348-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="51348-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="51348-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

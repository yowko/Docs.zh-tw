---
title: ICorDebugProcess7 介面
ms.date: 03/30/2017
api_name:
- ICorDebugProcess7
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 71aee5f3-5e10-44fa-be69-6d8a475f2c14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d73da04242bfe5a4958a62d2a48b609b474309
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987671"
---
# <a name="icordebugprocess7-interface"></a><span data-ttu-id="64d5d-102">ICorDebugProcess7 介面</span><span class="sxs-lookup"><span data-stu-id="64d5d-102">ICorDebugProcess7 Interface</span></span>
<span data-ttu-id="64d5d-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="64d5d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="64d5d-104">提供用來設定偵錯工具的方法，以控制代碼目標處理序中的記憶體中中繼資料更新。</span><span class="sxs-lookup"><span data-stu-id="64d5d-104">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64d5d-105">方法</span><span class="sxs-lookup"><span data-stu-id="64d5d-105">Methods</span></span>  
  
|<span data-ttu-id="64d5d-106">方法</span><span class="sxs-lookup"><span data-stu-id="64d5d-106">Method</span></span>|<span data-ttu-id="64d5d-107">描述</span><span class="sxs-lookup"><span data-stu-id="64d5d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64d5d-108">SetWriteableMetadataUpdateMode 方法</span><span class="sxs-lookup"><span data-stu-id="64d5d-108">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)|<span data-ttu-id="64d5d-109">設定一個值，以判定偵錯工具如何處理對目標處理序中之中繼資料的記憶體中更新。</span><span class="sxs-lookup"><span data-stu-id="64d5d-109">Sets a value that determines how the debugger handles in-memory updates to metadata within the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64d5d-110">備註</span><span class="sxs-lookup"><span data-stu-id="64d5d-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d5d-111">需求</span><span class="sxs-lookup"><span data-stu-id="64d5d-111">Requirements</span></span>  
 <span data-ttu-id="64d5d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64d5d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d5d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64d5d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64d5d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64d5d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64d5d-115">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d5d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d5d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64d5d-116">See also</span></span>

- [<span data-ttu-id="64d5d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="64d5d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="64d5d-118">偵錯</span><span class="sxs-lookup"><span data-stu-id="64d5d-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

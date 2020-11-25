---
title: ICorDebugObjectEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: 9400c4fa3ddcefef923d7bcfaae80e2cef62dc7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695461"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="85676-102">ICorDebugObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="85676-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="85676-103">會執行 ICorDebugEnum 方法，並依 (Rva) 的相對虛擬位址來列舉物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="85676-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85676-104">方法</span><span class="sxs-lookup"><span data-stu-id="85676-104">Methods</span></span>  
  
|<span data-ttu-id="85676-105">方法</span><span class="sxs-lookup"><span data-stu-id="85676-105">Method</span></span>|<span data-ttu-id="85676-106">描述</span><span class="sxs-lookup"><span data-stu-id="85676-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85676-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="85676-107">Next Method</span></span>](icordebugobjectenum-next-method.md)|<span data-ttu-id="85676-108">從目前位置開始，取得列舉中指定之物件數目的 Rva。</span><span class="sxs-lookup"><span data-stu-id="85676-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85676-109">備註</span><span class="sxs-lookup"><span data-stu-id="85676-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85676-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="85676-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85676-111">需求</span><span class="sxs-lookup"><span data-stu-id="85676-111">Requirements</span></span>  

 <span data-ttu-id="85676-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85676-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85676-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85676-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85676-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85676-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85676-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85676-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85676-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85676-116">See also</span></span>

- [<span data-ttu-id="85676-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="85676-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

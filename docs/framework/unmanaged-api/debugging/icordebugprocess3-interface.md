---
title: ICorDebugProcess3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3
helpviewer_keywords:
- ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type:
- apiref
ms.openlocfilehash: ef8dbd5253c02355f85fba626fa7e68ed62df4bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686439"
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="31da5-102">ICorDebugProcess3 介面</span><span class="sxs-lookup"><span data-stu-id="31da5-102">ICorDebugProcess3 Interface</span></span>

<span data-ttu-id="31da5-103">控制自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="31da5-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31da5-104">方法</span><span class="sxs-lookup"><span data-stu-id="31da5-104">Methods</span></span>  
  
|<span data-ttu-id="31da5-105">方法</span><span class="sxs-lookup"><span data-stu-id="31da5-105">Method</span></span>|<span data-ttu-id="31da5-106">描述</span><span class="sxs-lookup"><span data-stu-id="31da5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31da5-107">SetEnableCustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="31da5-107">SetEnableCustomNotification Method</span></span>](icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="31da5-108">啟用及停用指定類型的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="31da5-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31da5-109">備註</span><span class="sxs-lookup"><span data-stu-id="31da5-109">Remarks</span></span>  

 <span data-ttu-id="31da5-110">這個介面會以邏輯方式擴充 ICorDebugProcess 和 ICorDebugProcess2 介面。</span><span class="sxs-lookup"><span data-stu-id="31da5-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31da5-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="31da5-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31da5-112">需求</span><span class="sxs-lookup"><span data-stu-id="31da5-112">Requirements</span></span>  

 <span data-ttu-id="31da5-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31da5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31da5-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31da5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31da5-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31da5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31da5-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31da5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31da5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31da5-117">See also</span></span>

- [<span data-ttu-id="31da5-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="31da5-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="31da5-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="31da5-119">Debugging</span></span>](index.md)

---
title: ICorDebugInternalFrame Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45a710e6d8be4a041d9852585ea83fea85376f66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413822"
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="b1790-102">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="b1790-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="b1790-103">代表執行階段內部堆疊上的框架。</span><span class="sxs-lookup"><span data-stu-id="b1790-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="b1790-104">這個介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="b1790-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1790-105">方法</span><span class="sxs-lookup"><span data-stu-id="b1790-105">Methods</span></span>  
  
|<span data-ttu-id="b1790-106">方法</span><span class="sxs-lookup"><span data-stu-id="b1790-106">Method</span></span>|<span data-ttu-id="b1790-107">描述</span><span class="sxs-lookup"><span data-stu-id="b1790-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1790-108">GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="b1790-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="b1790-109">取得這個內部框架的類型。</span><span class="sxs-lookup"><span data-stu-id="b1790-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1790-110">備註</span><span class="sxs-lookup"><span data-stu-id="b1790-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1790-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b1790-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1790-112">需求</span><span class="sxs-lookup"><span data-stu-id="b1790-112">Requirements</span></span>  
 <span data-ttu-id="b1790-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1790-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1790-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1790-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1790-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1790-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1790-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1790-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1790-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1790-117">See Also</span></span>  
 [<span data-ttu-id="b1790-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b1790-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

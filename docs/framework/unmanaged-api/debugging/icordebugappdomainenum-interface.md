---
title: ICorDebugAppDomainEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
ms.openlocfilehash: 9fb849c78636d5e29f58a70f59aa4cb3cd22df40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784744"
---
# <a name="icordebugappdomainenum-interface"></a><span data-ttu-id="1e40e-102">ICorDebugAppDomainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1e40e-102">ICorDebugAppDomainEnum Interface</span></span>

<span data-ttu-id="1e40e-103">提供 `Next` 方法，它會從列舉中的下一個位置開始，傳回指定數目的 `ICorDebugAppDomainEnum` 值。</span><span class="sxs-lookup"><span data-stu-id="1e40e-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="1e40e-104">這個介面是 "ICorDebugEnum" 的子類別。</span><span class="sxs-lookup"><span data-stu-id="1e40e-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e40e-105">方法</span><span class="sxs-lookup"><span data-stu-id="1e40e-105">Methods</span></span>  
  
|<span data-ttu-id="1e40e-106">方法</span><span class="sxs-lookup"><span data-stu-id="1e40e-106">Method</span></span>|<span data-ttu-id="1e40e-107">描述</span><span class="sxs-lookup"><span data-stu-id="1e40e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e40e-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="1e40e-108">Next Method</span></span>](icordebugappdomainenum-next-method.md)|<span data-ttu-id="1e40e-109">從目前的資料指標位置開始，取得集合中指定的應用程式域數目。</span><span class="sxs-lookup"><span data-stu-id="1e40e-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e40e-110">備註</span><span class="sxs-lookup"><span data-stu-id="1e40e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e40e-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1e40e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e40e-112">需求</span><span class="sxs-lookup"><span data-stu-id="1e40e-112">Requirements</span></span>  
 <span data-ttu-id="1e40e-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e40e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e40e-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e40e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e40e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e40e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e40e-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e40e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e40e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e40e-117">See also</span></span>

- [<span data-ttu-id="1e40e-118">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="1e40e-118">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="1e40e-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1e40e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

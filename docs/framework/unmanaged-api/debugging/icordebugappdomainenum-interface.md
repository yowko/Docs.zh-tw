---
title: ICorDebugAppDomainEnum Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf8db3b02ba4766d046fc549eec8add31f51069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407916"
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="89502-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="89502-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="89502-103">提供`Next`方法，這個方法會傳回指定的數目的`ICorDebugAppDomainEnum`開始列舉中的下一個位置的值。</span><span class="sxs-lookup"><span data-stu-id="89502-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="89502-104">這個介面是 「 ICorDebugEnum"的子類別。</span><span class="sxs-lookup"><span data-stu-id="89502-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89502-105">方法</span><span class="sxs-lookup"><span data-stu-id="89502-105">Methods</span></span>  
  
|<span data-ttu-id="89502-106">方法</span><span class="sxs-lookup"><span data-stu-id="89502-106">Method</span></span>|<span data-ttu-id="89502-107">描述</span><span class="sxs-lookup"><span data-stu-id="89502-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89502-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="89502-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="89502-109">從集合中，從目前游標位置開始，取得指定的應用程式定義域數目。</span><span class="sxs-lookup"><span data-stu-id="89502-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89502-110">備註</span><span class="sxs-lookup"><span data-stu-id="89502-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89502-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="89502-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89502-112">需求</span><span class="sxs-lookup"><span data-stu-id="89502-112">Requirements</span></span>  
 <span data-ttu-id="89502-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89502-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89502-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89502-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89502-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89502-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89502-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89502-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89502-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89502-117">See Also</span></span>  
 [<span data-ttu-id="89502-118">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="89502-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="89502-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="89502-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

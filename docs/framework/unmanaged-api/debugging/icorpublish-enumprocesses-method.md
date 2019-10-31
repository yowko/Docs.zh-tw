---
title: ICorPublish::EnumProcesses 方法
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 5f0dd814ad5adfa1b0dd7199530a3f993634a548
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121789"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="f97a6-102">ICorPublish::EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="f97a6-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="f97a6-103">Gets an enumerator for the managed processes running on this computer.</span><span class="sxs-lookup"><span data-stu-id="f97a6-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97a6-104">語法</span><span class="sxs-lookup"><span data-stu-id="f97a6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f97a6-105">參數</span><span class="sxs-lookup"><span data-stu-id="f97a6-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="f97a6-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span><span class="sxs-lookup"><span data-stu-id="f97a6-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="f97a6-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span><span class="sxs-lookup"><span data-stu-id="f97a6-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="f97a6-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span><span class="sxs-lookup"><span data-stu-id="f97a6-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f97a6-109">備註</span><span class="sxs-lookup"><span data-stu-id="f97a6-109">Remarks</span></span>  
 <span data-ttu-id="f97a6-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span><span class="sxs-lookup"><span data-stu-id="f97a6-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="f97a6-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span><span class="sxs-lookup"><span data-stu-id="f97a6-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="f97a6-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span><span class="sxs-lookup"><span data-stu-id="f97a6-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="f97a6-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span><span class="sxs-lookup"><span data-stu-id="f97a6-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f97a6-114">需求</span><span class="sxs-lookup"><span data-stu-id="f97a6-114">Requirements</span></span>  
 <span data-ttu-id="f97a6-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f97a6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f97a6-116">**Header:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f97a6-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f97a6-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f97a6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f97a6-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f97a6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f97a6-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f97a6-119">See also</span></span>

- [<span data-ttu-id="f97a6-120">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="f97a6-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

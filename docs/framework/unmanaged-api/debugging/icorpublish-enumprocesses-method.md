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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb4096b0ae083e0b6c0598ea18cc8b33c2fdfe3e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116291"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="b4584-102">ICorPublish::EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="b4584-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="b4584-103">取得此電腦上執行的受管理處理程序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b4584-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4584-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4584-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4584-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4584-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="b4584-106">值為[COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)列舉，指定要擷取的程序的類型。</span><span class="sxs-lookup"><span data-stu-id="b4584-106">A value of the [COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="b4584-107">在目前的版本中，只有 COR_PUB_MANAGEDONLY 是有效的。</span><span class="sxs-lookup"><span data-stu-id="b4584-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="b4584-108">位址指標[ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)是列舉值的處理程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4584-108">A pointer to the address of an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4584-109">備註</span><span class="sxs-lookup"><span data-stu-id="b4584-109">Remarks</span></span>  
 <span data-ttu-id="b4584-110">處理序的列舉值的集合為基礎之處理序正在執行時的快照集`EnumProcesses`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b4584-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="b4584-111">列舉值將不會包含任何處理序終止之前或之後啟動`EnumProcesses`呼叫。</span><span class="sxs-lookup"><span data-stu-id="b4584-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="b4584-112">`EnumProcesses`可能會超過一次呼叫方法，這[ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)建立新的最新集合的程序的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b4584-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="b4584-113">現有的集合將不會受到的後續呼叫`EnumProcesses`方法。</span><span class="sxs-lookup"><span data-stu-id="b4584-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4584-114">需求</span><span class="sxs-lookup"><span data-stu-id="b4584-114">Requirements</span></span>  
 <span data-ttu-id="b4584-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4584-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4584-116">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b4584-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b4584-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4584-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b4584-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b4584-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b4584-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4584-119">See also</span></span>

- [<span data-ttu-id="b4584-120">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="b4584-120">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)

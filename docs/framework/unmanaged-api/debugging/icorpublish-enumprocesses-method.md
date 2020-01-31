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
ms.openlocfilehash: 5f785b22a3fbda6403c124ec70757b16f5335907
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790760"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="9e77d-102">ICorPublish::EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="9e77d-102">ICorPublish::EnumProcesses Method</span></span>
<span data-ttu-id="9e77d-103">取得在這部電腦上執行之 managed 進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9e77d-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e77d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e77d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e77d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e77d-105">Parameters</span></span>  
 `Type`  
 <span data-ttu-id="9e77d-106">[COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md)列舉的值，指定要抓取的進程類型。</span><span class="sxs-lookup"><span data-stu-id="9e77d-106">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="9e77d-107">在目前的版本中，只有 COR_PUB_MANAGEDONLY 有效。</span><span class="sxs-lookup"><span data-stu-id="9e77d-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="9e77d-108">[ICorPublishProcessEnum](icorpublishprocessenum-interface.md)實例位址的指標，這是進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="9e77d-108">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e77d-109">備註</span><span class="sxs-lookup"><span data-stu-id="9e77d-109">Remarks</span></span>  
 <span data-ttu-id="9e77d-110">列舉值的進程集合是以呼叫 `EnumProcesses` 方法時正在執行之進程的快照集為基礎。</span><span class="sxs-lookup"><span data-stu-id="9e77d-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="9e77d-111">列舉值不會包含呼叫 `EnumProcesses` 之後終止或啟動的任何進程。</span><span class="sxs-lookup"><span data-stu-id="9e77d-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="9e77d-112">可以在這個[ICorPublish](icorpublish-interface.md)實例上多次呼叫 `EnumProcesses` 方法，以建立最新的進程集合。</span><span class="sxs-lookup"><span data-stu-id="9e77d-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="9e77d-113">`EnumProcesses` 方法的後續呼叫將不會影響現有的集合。</span><span class="sxs-lookup"><span data-stu-id="9e77d-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e77d-114">需求</span><span class="sxs-lookup"><span data-stu-id="9e77d-114">Requirements</span></span>  
 <span data-ttu-id="9e77d-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e77d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e77d-116">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="9e77d-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9e77d-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e77d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e77d-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e77d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e77d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e77d-119">See also</span></span>

- [<span data-ttu-id="9e77d-120">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="9e77d-120">ICorPublish Interface</span></span>](icorpublish-interface.md)

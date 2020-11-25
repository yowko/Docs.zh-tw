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
ms.openlocfilehash: 297f672097dd6561a971608f368369c623532907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716911"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="fbda3-102">ICorPublish::EnumProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="fbda3-102">ICorPublish::EnumProcesses Method</span></span>

<span data-ttu-id="fbda3-103">取得在這部電腦上執行之 managed 進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fbda3-103">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbda3-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbda3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbda3-105">參數</span><span class="sxs-lookup"><span data-stu-id="fbda3-105">Parameters</span></span>  

 `Type`  
 <span data-ttu-id="fbda3-106">[COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md)列舉值，這個值會指定要抓取的進程類型。</span><span class="sxs-lookup"><span data-stu-id="fbda3-106">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="fbda3-107">在目前的版本中，只有 COR_PUB_MANAGEDONLY 有效。</span><span class="sxs-lookup"><span data-stu-id="fbda3-107">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="fbda3-108">[ICorPublishProcessEnum](icorpublishprocessenum-interface.md)實例的位址指標，這個實例是進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fbda3-108">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbda3-109">備註</span><span class="sxs-lookup"><span data-stu-id="fbda3-109">Remarks</span></span>  

 <span data-ttu-id="fbda3-110">列舉值的處理常式集合是以呼叫方法時正在執行之進程的快照集為基礎 `EnumProcesses` 。</span><span class="sxs-lookup"><span data-stu-id="fbda3-110">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="fbda3-111">列舉值將不會包含在呼叫之後終止或啟動的任何處理程式 `EnumProcesses` 。</span><span class="sxs-lookup"><span data-stu-id="fbda3-111">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="fbda3-112">可以 `EnumProcesses` 在這個 [ICorPublish](icorpublish-interface.md) 實例上多次呼叫方法，以建立新的最新處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="fbda3-112">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="fbda3-113">後續的方法呼叫將不會影響現有的集合 `EnumProcesses` 。</span><span class="sxs-lookup"><span data-stu-id="fbda3-113">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbda3-114">需求</span><span class="sxs-lookup"><span data-stu-id="fbda3-114">Requirements</span></span>  

 <span data-ttu-id="fbda3-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbda3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbda3-116">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="fbda3-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fbda3-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbda3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbda3-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbda3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbda3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbda3-119">See also</span></span>

- [<span data-ttu-id="fbda3-120">ICorPublish 介面</span><span class="sxs-lookup"><span data-stu-id="fbda3-120">ICorPublish Interface</span></span>](icorpublish-interface.md)

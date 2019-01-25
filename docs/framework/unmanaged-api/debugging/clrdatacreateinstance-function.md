---
title: CLRDataCreateInstance 函式
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22d9bf286a2241b0c1c5512e29532a01032cb3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648863"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="03455-102">CLRDataCreateInstance 函式</span><span class="sxs-lookup"><span data-stu-id="03455-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="03455-103">建立指定的目標項目介面物件。</span><span class="sxs-lookup"><span data-stu-id="03455-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03455-104">語法</span><span class="sxs-lookup"><span data-stu-id="03455-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03455-105">參數</span><span class="sxs-lookup"><span data-stu-id="03455-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="03455-106">[in]要具現化的介面識別項。</span><span class="sxs-lookup"><span data-stu-id="03455-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="03455-107">[in]使用者實作的指標[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)物件，表示要建立的介面物件的目標項目。</span><span class="sxs-lookup"><span data-stu-id="03455-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="03455-108">[out]傳回的介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="03455-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03455-109">備註</span><span class="sxs-lookup"><span data-stu-id="03455-109">Remarks</span></span>  
 <span data-ttu-id="03455-110">`ICLRDataTarget`物件藉由偵錯的應用程式的寫入器。</span><span class="sxs-lookup"><span data-stu-id="03455-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="03455-111">實作取決於所表示的目標項目類型。</span><span class="sxs-lookup"><span data-stu-id="03455-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="03455-112">目標項目可能是處理程序、 記憶體傾印、 遠端電腦，等等。</span><span class="sxs-lookup"><span data-stu-id="03455-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03455-113">需求</span><span class="sxs-lookup"><span data-stu-id="03455-113">Requirements</span></span>  
 <span data-ttu-id="03455-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03455-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03455-115">**標頭：** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="03455-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="03455-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03455-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03455-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03455-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03455-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03455-118">See also</span></span>
- [<span data-ttu-id="03455-119">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="03455-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

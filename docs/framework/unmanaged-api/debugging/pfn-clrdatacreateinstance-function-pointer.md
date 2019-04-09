---
title: PFN_CLRDataCreateInstance 函式指標
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff2ddb1e98f3455c6915acf8149f528176228425
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177979"
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="07be9-102">PFN_CLRDataCreateInstance 函式指標</span><span class="sxs-lookup"><span data-stu-id="07be9-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="07be9-103">指向函式來建立指定的目標項目介面物件。</span><span class="sxs-lookup"><span data-stu-id="07be9-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07be9-104">語法</span><span class="sxs-lookup"><span data-stu-id="07be9-104">Syntax</span></span>  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07be9-105">參數</span><span class="sxs-lookup"><span data-stu-id="07be9-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="07be9-106">[in]要具現化的介面識別項。</span><span class="sxs-lookup"><span data-stu-id="07be9-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="07be9-107">[in]使用者實作的指標[ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)物件，表示要建立的介面物件的目標項目。</span><span class="sxs-lookup"><span data-stu-id="07be9-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="07be9-108">[out]傳回的介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="07be9-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07be9-109">備註</span><span class="sxs-lookup"><span data-stu-id="07be9-109">Remarks</span></span>  
 <span data-ttu-id="07be9-110">`ICLRDataTarget`物件藉由偵錯的應用程式的寫入器。</span><span class="sxs-lookup"><span data-stu-id="07be9-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="07be9-111">實作取決於所表示的目標項目類型。</span><span class="sxs-lookup"><span data-stu-id="07be9-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="07be9-112">目標項目可能是處理程序、 記憶體傾印、 遠端電腦，等等。</span><span class="sxs-lookup"><span data-stu-id="07be9-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07be9-113">需求</span><span class="sxs-lookup"><span data-stu-id="07be9-113">Requirements</span></span>  
 <span data-ttu-id="07be9-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07be9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07be9-115">**標頭：** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="07be9-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="07be9-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07be9-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="07be9-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="07be9-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07be9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07be9-118">See also</span></span>

- [<span data-ttu-id="07be9-119">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="07be9-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

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
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179355"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="2e9ec-102">CLRDataCreateInstance 函式</span><span class="sxs-lookup"><span data-stu-id="2e9ec-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="2e9ec-103">為指定的目標項創建介面物件。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e9ec-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e9ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e9ec-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="2e9ec-106">[在]要具現化的介面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="2e9ec-107">[在]指向使用者實現的[ICLRDataTarget](iclrdatatarget-interface.md)物件的指標，該物件表示要為其創建介面物件的目標項。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="2e9ec-108">[出]指向返回介面物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e9ec-109">備註</span><span class="sxs-lookup"><span data-stu-id="2e9ec-109">Remarks</span></span>  
 <span data-ttu-id="2e9ec-110">該`ICLRDataTarget`物件由調試應用程式的編寫器實現。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="2e9ec-111">實現取決於表示的目標項的類型。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="2e9ec-112">目標項可以是進程、記憶體傾印、遠端電腦等。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e9ec-113">需求</span><span class="sxs-lookup"><span data-stu-id="2e9ec-113">Requirements</span></span>  
 <span data-ttu-id="2e9ec-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e9ec-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9ec-115">**標題：** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="2e9ec-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="2e9ec-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e9ec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e9ec-117">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e9ec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9ec-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e9ec-118">See also</span></span>

- [<span data-ttu-id="2e9ec-119">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="2e9ec-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

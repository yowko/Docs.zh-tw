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
ms.openlocfilehash: a5d44f9b5dc42147959d3f1d127a64d39258f515
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274269"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="874b4-102">CLRDataCreateInstance 函式</span><span class="sxs-lookup"><span data-stu-id="874b4-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="874b4-103">為指定的目標專案建立介面物件。</span><span class="sxs-lookup"><span data-stu-id="874b4-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="874b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="874b4-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="874b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="874b4-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="874b4-106">在要具現化之介面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="874b4-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="874b4-107">在使用者實[ICLRDataTarget](iclrdatatarget-interface.md)物件的指標，表示要建立介面物件的目標專案。</span><span class="sxs-lookup"><span data-stu-id="874b4-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="874b4-108">脫銷傳回之介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="874b4-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="874b4-109">備註</span><span class="sxs-lookup"><span data-stu-id="874b4-109">Remarks</span></span>  
 <span data-ttu-id="874b4-110">`ICLRDataTarget`物件是由偵錯工具的寫入器所執行。</span><span class="sxs-lookup"><span data-stu-id="874b4-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="874b4-111">此實作為相依于所表示的目標專案類型。</span><span class="sxs-lookup"><span data-stu-id="874b4-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="874b4-112">目標專案可能是進程、記憶體傾印、遠端電腦等等。</span><span class="sxs-lookup"><span data-stu-id="874b4-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="874b4-113">需求</span><span class="sxs-lookup"><span data-stu-id="874b4-113">Requirements</span></span>  
 <span data-ttu-id="874b4-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="874b4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="874b4-115">**標頭：** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="874b4-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="874b4-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="874b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="874b4-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="874b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874b4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="874b4-118">See also</span></span>

- [<span data-ttu-id="874b4-119">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="874b4-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

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
ms.openlocfilehash: 68a5b8bb1568f10699653479357b02b2e847cc02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671963"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="0d908-102">PFN_CLRDataCreateInstance 函式指標</span><span class="sxs-lookup"><span data-stu-id="0d908-102">PFN_CLRDataCreateInstance Function Pointer</span></span>

<span data-ttu-id="0d908-103">指向函式，該函式會建立指定之目標專案的介面物件。</span><span class="sxs-lookup"><span data-stu-id="0d908-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d908-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d908-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d908-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d908-105">Parameters</span></span>  

 `iid`  
 <span data-ttu-id="0d908-106">在要具現化之介面的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0d908-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="0d908-107">在使用者實 [ICLRDataTarget](iclrdatatarget-interface.md) 物件的指標，代表要建立介面物件的目標專案。</span><span class="sxs-lookup"><span data-stu-id="0d908-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="0d908-108">擴展傳回之介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="0d908-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d908-109">備註</span><span class="sxs-lookup"><span data-stu-id="0d908-109">Remarks</span></span>  

 <span data-ttu-id="0d908-110">`ICLRDataTarget`物件是由偵錯工具的寫入器所執行。</span><span class="sxs-lookup"><span data-stu-id="0d908-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="0d908-111">此執行取決於所表示的目標專案類型。</span><span class="sxs-lookup"><span data-stu-id="0d908-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="0d908-112">目標專案可能是進程、記憶體傾印、遠端電腦等等。</span><span class="sxs-lookup"><span data-stu-id="0d908-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d908-113">需求</span><span class="sxs-lookup"><span data-stu-id="0d908-113">Requirements</span></span>  

 <span data-ttu-id="0d908-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d908-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d908-115">**標頭：** ClrData .idl</span><span class="sxs-lookup"><span data-stu-id="0d908-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="0d908-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d908-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d908-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d908-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d908-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d908-118">See also</span></span>

- [<span data-ttu-id="0d908-119">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="0d908-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

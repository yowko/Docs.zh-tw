---
title: ICLRDataTarget2::FreeVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: 0a36af5b411673081e74aa243ec8e0f8f876f238
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860480"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="6fc18-102">ICLRDataTarget2::FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="6fc18-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="6fc18-103">由 common language runtime （CLR）資料存取服務呼叫，以釋放先前在目標進程的位址空間中配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="6fc18-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fc18-104">語法</span><span class="sxs-lookup"><span data-stu-id="6fc18-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fc18-105">參數</span><span class="sxs-lookup"><span data-stu-id="6fc18-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="6fc18-106">在`CLRDATA_ADDRESS`值，指定要釋放之記憶體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="6fc18-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="6fc18-107">在要釋放的記憶體大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6fc18-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="6fc18-108">在控制記憶體釋放的旗標。</span><span class="sxs-lookup"><span data-stu-id="6fc18-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="6fc18-109">請參閱 Win32 `VirtualFree`函數。</span><span class="sxs-lookup"><span data-stu-id="6fc18-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fc18-110">備註</span><span class="sxs-lookup"><span data-stu-id="6fc18-110">Remarks</span></span>  
 <span data-ttu-id="6fc18-111">`FreeVirtual`方法可做為 Win32 `VirtualFree`函式的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="6fc18-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="6fc18-112">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="6fc18-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fc18-113">需求</span><span class="sxs-lookup"><span data-stu-id="6fc18-113">Requirements</span></span>  
 <span data-ttu-id="6fc18-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fc18-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fc18-115">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="6fc18-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6fc18-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fc18-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fc18-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fc18-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc18-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fc18-118">See also</span></span>

- [<span data-ttu-id="6fc18-119">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="6fc18-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="6fc18-120">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="6fc18-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)

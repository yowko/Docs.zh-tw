---
title: ICLRDataTarget::SetTLSValue 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
ms.openlocfilehash: 6c98fc93fd659ccfc0ccd42eec7d95382cf342f8
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860522"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="c6678-102">ICLRDataTarget::SetTLSValue 方法</span><span class="sxs-lookup"><span data-stu-id="c6678-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="c6678-103">設定目標進程中指定執行緒的執行緒區域儲存區（TLS）中的值。</span><span class="sxs-lookup"><span data-stu-id="c6678-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="c6678-104">這個方法是由 common language runtime （CLR）資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="c6678-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6678-105">語法</span><span class="sxs-lookup"><span data-stu-id="c6678-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6678-106">參數</span><span class="sxs-lookup"><span data-stu-id="c6678-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c6678-107">在目標進程中線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="c6678-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="c6678-108">在位置的索引。</span><span class="sxs-lookup"><span data-stu-id="c6678-108">[in] The index of the location.</span></span> <span data-ttu-id="c6678-109">這個值必須是指定之執行緒本機存放區中的有效索引。</span><span class="sxs-lookup"><span data-stu-id="c6678-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="c6678-110">在`CLRDATA_ADDRESS`值，指定要在指定的 TLS 位置中放置的值。</span><span class="sxs-lookup"><span data-stu-id="c6678-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6678-111">備註</span><span class="sxs-lookup"><span data-stu-id="c6678-111">Remarks</span></span>  
 <span data-ttu-id="c6678-112">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="c6678-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6678-113">需求</span><span class="sxs-lookup"><span data-stu-id="c6678-113">Requirements</span></span>  
 <span data-ttu-id="c6678-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6678-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6678-115">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="c6678-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c6678-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6678-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6678-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6678-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6678-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="c6678-118">See also</span></span>

- [<span data-ttu-id="c6678-119">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="c6678-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)

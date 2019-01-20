---
title: IXCLRDataModule::Request 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 0226a11b142515296d976e3d645cb2475d634420
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416338"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="4d111-102">IXCLRDataModule::Request 方法</span><span class="sxs-lookup"><span data-stu-id="4d111-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="4d111-103">填入指定模組的資料緩衝區的要求。</span><span class="sxs-lookup"><span data-stu-id="4d111-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="4d111-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d111-104">Syntax</span></span>
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

### <a name="parameters"></a><span data-ttu-id="4d111-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d111-105">Parameters</span></span>

<span data-ttu-id="4d111-106">`reqCode` [in]要求傳送的型別。</span><span class="sxs-lookup"><span data-stu-id="4d111-106">`reqCode` [in] Request type to be sent.</span></span>

<span data-ttu-id="4d111-107">`inBufferSize` [in] 要傳入的輸入緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="4d111-107">`inBufferSize` [in] size of the input buffer to be passed in.</span></span>

<span data-ttu-id="4d111-108">`inBuffer` [in、 size_is(inBufferSize)]若要在要求中傳送未經處理資料的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="4d111-108">`inBuffer` [in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

<span data-ttu-id="4d111-109">`outBufferSize` [in]輸出緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="4d111-109">`outBufferSize` [in] Size of the output buffer.</span></span>

<span data-ttu-id="4d111-110">`outBuffer` [out，size_is(outBufferSize)]用來儲存要求回應的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="4d111-110">`outBuffer` [out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="4d111-111">備註</span><span class="sxs-lookup"><span data-stu-id="4d111-111">Remarks</span></span>

<span data-ttu-id="4d111-112">提供的方法是一部分`IXCLRDataModule`介面，並對應至 36th 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="4d111-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d111-113">需求</span><span class="sxs-lookup"><span data-stu-id="4d111-113">Requirements</span></span>

<span data-ttu-id="4d111-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d111-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4d111-115">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="4d111-115">**Header:** None</span></span>   
<span data-ttu-id="4d111-116">**程式庫：** 無</span><span class="sxs-lookup"><span data-stu-id="4d111-116">**Library:** None</span></span>  
<span data-ttu-id="4d111-117">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4d111-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="4d111-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d111-118">See Also</span></span>
- [<span data-ttu-id="4d111-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="4d111-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="4d111-120">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="4d111-120">IXCLRDataModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)

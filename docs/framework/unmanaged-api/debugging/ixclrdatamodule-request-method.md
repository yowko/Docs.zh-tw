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
ms.openlocfilehash: 755063ca6da29a2e4733dd653306192ac0434ec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775449"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="e8c2e-102">IXCLRDataModule::Request 方法</span><span class="sxs-lookup"><span data-stu-id="e8c2e-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="e8c2e-103">填入指定模組的資料緩衝區的要求。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e8c2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8c2e-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="e8c2e-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8c2e-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="e8c2e-106">[in]要求傳送的型別。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="e8c2e-107">[in] 要傳入的輸入緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="e8c2e-108">[in、 size_is(inBufferSize)]若要在要求中傳送未經處理資料的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="e8c2e-109">[in]輸出緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="e8c2e-110">[out，size_is(outBufferSize)]用來儲存要求回應的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8c2e-111">備註</span><span class="sxs-lookup"><span data-stu-id="e8c2e-111">Remarks</span></span>

<span data-ttu-id="e8c2e-112">提供的方法是一部分`IXCLRDataModule`介面，並對應至 36th 虛擬方法表的位置。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 36th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8c2e-113">需求</span><span class="sxs-lookup"><span data-stu-id="e8c2e-113">Requirements</span></span>

<span data-ttu-id="e8c2e-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8c2e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="e8c2e-115">**標頭：** 無**程式庫：** 無 **.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e8c2e-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e8c2e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8c2e-116">See also</span></span>

- [<span data-ttu-id="e8c2e-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="e8c2e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="e8c2e-118">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="e8c2e-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
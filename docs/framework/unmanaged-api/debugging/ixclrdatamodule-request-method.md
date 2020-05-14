---
title: IXCLRDataModule：： Request 方法
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
ms.openlocfilehash: 44ee4fc7fc2368b65f6f2fffe6ac239beddc6293
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395273"
---
# <a name="ixclrdatamodulerequest-method"></a><span data-ttu-id="c0f12-102">IXCLRDataModule：： Request 方法</span><span class="sxs-lookup"><span data-stu-id="c0f12-102">IXCLRDataModule::Request Method</span></span>

<span data-ttu-id="c0f12-103">要求填入模組資料所提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c0f12-103">Requests to populate the buffer given with the module's data.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="c0f12-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0f12-104">Syntax</span></span>

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a><span data-ttu-id="c0f12-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0f12-105">Parameters</span></span>

`reqCode`\
<span data-ttu-id="c0f12-106">在要傳送的要求類型。</span><span class="sxs-lookup"><span data-stu-id="c0f12-106">[in] Request type to be sent.</span></span>

`inBufferSize`\
<span data-ttu-id="c0f12-107">[in] 要傳入之輸入緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="c0f12-107">[in] size of the input buffer to be passed in.</span></span>

`inBuffer`\
<span data-ttu-id="c0f12-108">[in，size_is （inBufferSize）]要在要求中傳送之原始資料的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="c0f12-108">[in, size_is(inBufferSize)] Buffer pointer for the raw data to be sent in the request.</span></span>

`outBufferSize`\
<span data-ttu-id="c0f12-109">在輸出緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="c0f12-109">[in] Size of the output buffer.</span></span>

`outBuffer`\
<span data-ttu-id="c0f12-110">[out，size_is （outBufferSize）]用來儲存要求回應的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="c0f12-110">[out, size_is(outBufferSize)] Buffer pointer to used to store the request response.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0f12-111">備註</span><span class="sxs-lookup"><span data-stu-id="c0f12-111">Remarks</span></span>

<span data-ttu-id="c0f12-112">提供的方法是介面的一部分 `IXCLRDataModule` ，而且會對應至虛擬方法資料表的37th 位置。</span><span class="sxs-lookup"><span data-stu-id="c0f12-112">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 37th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="c0f12-113">需求</span><span class="sxs-lookup"><span data-stu-id="c0f12-113">Requirements</span></span>

<span data-ttu-id="c0f12-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0f12-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="c0f12-115">**標頭：** 無**媒體櫃：** 無 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c0f12-115">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c0f12-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f12-116">See also</span></span>

- [<span data-ttu-id="c0f12-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="c0f12-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="c0f12-118">IXCLRDataModule 介面</span><span class="sxs-lookup"><span data-stu-id="c0f12-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)

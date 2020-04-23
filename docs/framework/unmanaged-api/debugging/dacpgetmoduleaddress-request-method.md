---
title: DacpGetModule 位址:請求方法
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102903"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="15253-102">DacpGetModule 位址:請求方法</span><span class="sxs-lookup"><span data-stu-id="15253-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="15253-103">執行請求,從給定的運行時結構填充結構。</span><span class="sxs-lookup"><span data-stu-id="15253-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="15253-104">語法</span><span class="sxs-lookup"><span data-stu-id="15253-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="15253-105">參數</span><span class="sxs-lookup"><span data-stu-id="15253-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="15253-106">[在]指向種子數據模組的指標。</span><span class="sxs-lookup"><span data-stu-id="15253-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="15253-107">備註</span><span class="sxs-lookup"><span data-stu-id="15253-107">Remarks</span></span>

<span data-ttu-id="15253-108">此結構位於運行時內,不會通過任何標頭或庫文件公開。</span><span class="sxs-lookup"><span data-stu-id="15253-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="15253-109">要使用它,最簡單的方法是模擬實現:</span><span class="sxs-lookup"><span data-stu-id="15253-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="15253-110">使用以下參數返回從呼叫`Request``IXCLRDataModule*`參數上的方法獲得的值:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="15253-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="15253-111">需求</span><span class="sxs-lookup"><span data-stu-id="15253-111">Requirements</span></span>

<span data-ttu-id="15253-112">**平臺:** 請參考[系統要求](../../../../docs/framework/get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="15253-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md)</span></span>\
<span data-ttu-id="15253-113">**標題:** 無。</span><span class="sxs-lookup"><span data-stu-id="15253-113">**Header:** None\</span></span>
<span data-ttu-id="15253-114">**庫:** 無。</span><span class="sxs-lookup"><span data-stu-id="15253-114">**Library:** None\</span></span>
<span data-ttu-id="15253-115">**.NET 框架版本:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15253-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="15253-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15253-116">See also</span></span>

- [<span data-ttu-id="15253-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="15253-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="15253-118">DacpGetModule 位址結構</span><span class="sxs-lookup"><span data-stu-id="15253-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)

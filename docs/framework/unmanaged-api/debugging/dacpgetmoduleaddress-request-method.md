---
title: DacpGetModule 位址：請求方法
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
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179204"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="ef405-102">DacpGetModule 位址：請求方法</span><span class="sxs-lookup"><span data-stu-id="ef405-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="ef405-103">執行請求，從給定的運行時結構填充結構。</span><span class="sxs-lookup"><span data-stu-id="ef405-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ef405-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef405-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="ef405-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef405-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="ef405-106">[在]指向種子資料模組的指標。</span><span class="sxs-lookup"><span data-stu-id="ef405-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef405-107">備註</span><span class="sxs-lookup"><span data-stu-id="ef405-107">Remarks</span></span>

<span data-ttu-id="ef405-108">此結構位於運行時內，不會通過任何標頭或庫檔公開。</span><span class="sxs-lookup"><span data-stu-id="ef405-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ef405-109">要使用它，最簡單的方法是類比實現：</span><span class="sxs-lookup"><span data-stu-id="ef405-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="ef405-110">使用以下參數返回從調用`Request``IXCLRDataModule*`參數上的方法獲得的值：`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="ef405-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="ef405-111">需求</span><span class="sxs-lookup"><span data-stu-id="ef405-111">Requirements</span></span>

<span data-ttu-id="ef405-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef405-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ef405-113">**標題：** 無**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="ef405-113">**Header:** None **Library:** None</span></span>  
<span data-ttu-id="ef405-114">**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ef405-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ef405-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef405-115">See also</span></span>

- [<span data-ttu-id="ef405-116">偵錯</span><span class="sxs-lookup"><span data-stu-id="ef405-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="ef405-117">達格格獲取模組位址介面</span><span class="sxs-lookup"><span data-stu-id="ef405-117">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)

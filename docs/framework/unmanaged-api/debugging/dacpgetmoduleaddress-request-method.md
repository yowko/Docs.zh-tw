---
title: DacpGetModuleAddress::要求方法
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
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860847"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="e599a-102">DacpGetModuleAddress::要求方法</span><span class="sxs-lookup"><span data-stu-id="e599a-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="e599a-103">執行要求，以從指定的執行時間結構填入結構。</span><span class="sxs-lookup"><span data-stu-id="e599a-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e599a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e599a-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="e599a-105">參數</span><span class="sxs-lookup"><span data-stu-id="e599a-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="e599a-106">在種子資料模組的指標。</span><span class="sxs-lookup"><span data-stu-id="e599a-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="e599a-107">備註</span><span class="sxs-lookup"><span data-stu-id="e599a-107">Remarks</span></span>

<span data-ttu-id="e599a-108">這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="e599a-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="e599a-109">若要使用它，最簡單的方法是模擬此實作為：</span><span class="sxs-lookup"><span data-stu-id="e599a-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="e599a-110">使用下列參數，傳回從呼叫`Request` `IXCLRDataModule*`參數上的方法取得的值：`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="e599a-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="e599a-111">需求</span><span class="sxs-lookup"><span data-stu-id="e599a-111">Requirements</span></span>

<span data-ttu-id="e599a-112">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="e599a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="e599a-113">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="e599a-113">**Header:** None\</span></span>
<span data-ttu-id="e599a-114">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="e599a-114">**Library:** None\</span></span>
<span data-ttu-id="e599a-115">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e599a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e599a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e599a-116">See also</span></span>

- [<span data-ttu-id="e599a-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="e599a-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="e599a-118">DacpGetModuleAddress 結構</span><span class="sxs-lookup"><span data-stu-id="e599a-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)

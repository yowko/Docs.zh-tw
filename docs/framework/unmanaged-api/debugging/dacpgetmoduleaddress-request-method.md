---
title: DacpGetModuleAddress::Request Method
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
ms.openlocfilehash: 298620092c37b2c02332e9135f73584272e326bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111679"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="d47e2-102">DacpGetModuleAddress::Request Method</span><span class="sxs-lookup"><span data-stu-id="d47e2-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="d47e2-103">會執行要求，以填入指定的執行階段結構中的結構。</span><span class="sxs-lookup"><span data-stu-id="d47e2-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d47e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="d47e2-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="d47e2-105">參數</span><span class="sxs-lookup"><span data-stu-id="d47e2-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="d47e2-106">[in]種子資料模組指標。</span><span class="sxs-lookup"><span data-stu-id="d47e2-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="d47e2-107">備註</span><span class="sxs-lookup"><span data-stu-id="d47e2-107">Remarks</span></span>

<span data-ttu-id="d47e2-108">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="d47e2-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="d47e2-109">若要使用它，最簡單的方法是模擬的實作：</span><span class="sxs-lookup"><span data-stu-id="d47e2-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="d47e2-110">傳回從呼叫取得的值`Request`方法`IXCLRDataModule*`參數搭配下列參數：</span><span class="sxs-lookup"><span data-stu-id="d47e2-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters:</span></span> `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a><span data-ttu-id="d47e2-111">需求</span><span class="sxs-lookup"><span data-stu-id="d47e2-111">Requirements</span></span>

<span data-ttu-id="d47e2-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d47e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d47e2-113">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="d47e2-113">**Header:** None</span></span>     
<span data-ttu-id="d47e2-114">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="d47e2-114">**Library:** None</span></span>  
**<span data-ttu-id="d47e2-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="d47e2-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="d47e2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d47e2-116">See also</span></span>

- [<span data-ttu-id="d47e2-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="d47e2-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="d47e2-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="d47e2-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)
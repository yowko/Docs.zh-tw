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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965882"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="11fd9-102">DacpGetModuleAddress::Request Method</span><span class="sxs-lookup"><span data-stu-id="11fd9-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="11fd9-103">會執行要求，以填入指定的執行階段結構中的結構。</span><span class="sxs-lookup"><span data-stu-id="11fd9-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="11fd9-104">語法</span><span class="sxs-lookup"><span data-stu-id="11fd9-104">Syntax</span></span>

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="11fd9-105">參數</span><span class="sxs-lookup"><span data-stu-id="11fd9-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="11fd9-106">[in]種子資料模組指標。</span><span class="sxs-lookup"><span data-stu-id="11fd9-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="11fd9-107">備註</span><span class="sxs-lookup"><span data-stu-id="11fd9-107">Remarks</span></span>

<span data-ttu-id="11fd9-108">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="11fd9-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="11fd9-109">若要使用它，最簡單的方法是模擬的實作：</span><span class="sxs-lookup"><span data-stu-id="11fd9-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="11fd9-110">傳回從呼叫取得的值`Request`方法`IXCLRDataModule*`參數搭配下列參數： `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="11fd9-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="11fd9-111">需求</span><span class="sxs-lookup"><span data-stu-id="11fd9-111">Requirements</span></span>

<span data-ttu-id="11fd9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11fd9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="11fd9-113">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="11fd9-113">**Header:** None</span></span>     
<span data-ttu-id="11fd9-114">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="11fd9-114">**Library:** None</span></span>  
<span data-ttu-id="11fd9-115">**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="11fd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="11fd9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11fd9-116">See also</span></span>

- [<span data-ttu-id="11fd9-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="11fd9-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="11fd9-118">DacpGetModuleAddress Interface</span><span class="sxs-lookup"><span data-stu-id="11fd9-118">DacpGetModuleAddress Interface</span></span>](dacpgetmoduleaddress-structure.md)
---
title: DacpMethodDescData 結構
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 567dc3942f79b6bfd29338b9103083aa64e66451
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203193"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="1b9d3-102">DacpMethodDescData 結構</span><span class="sxs-lookup"><span data-stu-id="1b9d3-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="1b9d3-103">定義方法的執行階段資訊的傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1b9d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b9d3-104">Syntax</span></span>

```
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="1b9d3-105">成員</span><span class="sxs-lookup"><span data-stu-id="1b9d3-105">Members</span></span>

| <span data-ttu-id="1b9d3-106">成員</span><span class="sxs-lookup"><span data-stu-id="1b9d3-106">Member</span></span>                       | <span data-ttu-id="1b9d3-107">描述</span><span class="sxs-lookup"><span data-stu-id="1b9d3-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="1b9d3-108">指出執行階段是否有原生程式碼可用於指定具現化的方法。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="1b9d3-109">指出是否透過輕量型程式碼產生動態產生的方法。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="1b9d3-110">方法的方法資料表中的位置編號。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="1b9d3-111">方法的初始原生位址。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="1b9d3-112">供內部使用執行階段緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="1b9d3-113">指標`MethodDesc`在執行階段。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="1b9d3-114">若要追蹤方法內部使用執行階段緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="1b9d3-115">執行階段內部使用的模組資訊之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="1b9d3-116">與指定的方法相關聯的權杖。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="1b9d3-117">供內部使用執行階段的記憶體回收集合緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="1b9d3-118">供內部使用執行階段的記憶體回收集合緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="1b9d3-119">如果方法是動態的執行階段會使用這個緩衝區內部追蹤的資訊。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="1b9d3-120">用來填入每個要求時的原生程式碼位址結構。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="1b9d3-121">方法的最新的已檢測版本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="1b9d3-122">Rejit 要求的原生位址資訊。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="1b9d3-123">此方法已透過檢測 rejitted 的次數。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="1b9d3-124">備註</span><span class="sxs-lookup"><span data-stu-id="1b9d3-124">Remarks</span></span>

<span data-ttu-id="1b9d3-125">此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1b9d3-126">若要使用它，定義如上述所指定的結構。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b9d3-127">需求</span><span class="sxs-lookup"><span data-stu-id="1b9d3-127">Requirements</span></span>
<span data-ttu-id="1b9d3-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b9d3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1b9d3-129">**標頭：** None</span><span class="sxs-lookup"><span data-stu-id="1b9d3-129">**Header:** None</span></span>  
<span data-ttu-id="1b9d3-130">**LIBRARY:** None</span><span class="sxs-lookup"><span data-stu-id="1b9d3-130">**Library:** None</span></span>  
**<span data-ttu-id="1b9d3-131">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="1b9d3-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a><span data-ttu-id="1b9d3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b9d3-132">See also</span></span>

- [<span data-ttu-id="1b9d3-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="1b9d3-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="1b9d3-134">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="1b9d3-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="1b9d3-135">常見資料類型</span><span class="sxs-lookup"><span data-stu-id="1b9d3-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)

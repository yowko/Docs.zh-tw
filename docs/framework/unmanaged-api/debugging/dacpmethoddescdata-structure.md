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
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860812"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="30d8e-102">DacpMethodDescData 結構</span><span class="sxs-lookup"><span data-stu-id="30d8e-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="30d8e-103">為方法的執行時間資訊定義傳輸緩衝區。</span><span class="sxs-lookup"><span data-stu-id="30d8e-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="30d8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="30d8e-104">Syntax</span></span>

```cpp
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

## <a name="members"></a><span data-ttu-id="30d8e-105">成員</span><span class="sxs-lookup"><span data-stu-id="30d8e-105">Members</span></span>

| <span data-ttu-id="30d8e-106">member</span><span class="sxs-lookup"><span data-stu-id="30d8e-106">Member</span></span>                       | <span data-ttu-id="30d8e-107">描述</span><span class="sxs-lookup"><span data-stu-id="30d8e-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="30d8e-108">指出執行時間是否具有原生程式碼，可用於指定的方法具現化。</span><span class="sxs-lookup"><span data-stu-id="30d8e-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="30d8e-109">指出此方法是否透過輕量程式碼產生動態產生。</span><span class="sxs-lookup"><span data-stu-id="30d8e-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="30d8e-110">方法資料表中的方法位置編號。</span><span class="sxs-lookup"><span data-stu-id="30d8e-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="30d8e-111">方法的初始原生位址。</span><span class="sxs-lookup"><span data-stu-id="30d8e-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="30d8e-112">執行時間內部使用之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="30d8e-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="30d8e-113">執行時間中`MethodDesc`的指標。</span><span class="sxs-lookup"><span data-stu-id="30d8e-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="30d8e-114">執行時間內部用來追蹤方法之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="30d8e-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="30d8e-115">執行時間內部用來取得模組資訊之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="30d8e-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="30d8e-116">與指定方法相關聯的 Token。</span><span class="sxs-lookup"><span data-stu-id="30d8e-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="30d8e-117">執行時間內部使用之垃圾收集緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="30d8e-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="30d8e-118">執行時間內部使用之垃圾收集緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="30d8e-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="30d8e-119">如果方法是動態的，則執行時間會在內部使用此緩衝區進行資訊追蹤。</span><span class="sxs-lookup"><span data-stu-id="30d8e-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="30d8e-120">當指定原生程式碼位址時，用來填入每個要求的結構。</span><span class="sxs-lookup"><span data-stu-id="30d8e-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="30d8e-121">方法的最新檢測版本的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="30d8e-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="30d8e-122">Rejit 所要求之原生位址的資訊。</span><span class="sxs-lookup"><span data-stu-id="30d8e-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="30d8e-123">透過檢測 rejitted 方法的次數。</span><span class="sxs-lookup"><span data-stu-id="30d8e-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="30d8e-124">備註</span><span class="sxs-lookup"><span data-stu-id="30d8e-124">Remarks</span></span>

<span data-ttu-id="30d8e-125">這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。</span><span class="sxs-lookup"><span data-stu-id="30d8e-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="30d8e-126">若要使用它，請依照上面的指定定義結構。</span><span class="sxs-lookup"><span data-stu-id="30d8e-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="30d8e-127">需求</span><span class="sxs-lookup"><span data-stu-id="30d8e-127">Requirements</span></span>
<span data-ttu-id="30d8e-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30d8e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="30d8e-129">**標頭：** 無</span><span class="sxs-lookup"><span data-stu-id="30d8e-129">**Header:** None</span></span>  
<span data-ttu-id="30d8e-130">連結**庫：** 無</span><span class="sxs-lookup"><span data-stu-id="30d8e-130">**Library:** None</span></span>  
<span data-ttu-id="30d8e-131">**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="30d8e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="30d8e-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="30d8e-132">See also</span></span>

- [<span data-ttu-id="30d8e-133">偵錯</span><span class="sxs-lookup"><span data-stu-id="30d8e-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="30d8e-134">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="30d8e-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="30d8e-135">一般資料類型</span><span class="sxs-lookup"><span data-stu-id="30d8e-135">Common Data Types</span></span>](../common-data-types-unmanaged-api-reference.md)

---
title: WriteableMetadataUpdateMode 列舉
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- WriteableMetadataUpdateMode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6758f4d3-6bc7-4c99-8582-e9be00566784
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62e4328b75a7f6fecc28cd620ec3ac18460316c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111133"
---
# <a name="writeablemetadataupdatemode-enumeration"></a><span data-ttu-id="5d498-102">WriteableMetadataUpdateMode 列舉</span><span class="sxs-lookup"><span data-stu-id="5d498-102">WriteableMetadataUpdateMode Enumeration</span></span>
<span data-ttu-id="5d498-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="5d498-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5d498-104">提供值來指定偵錯工具是否可以看見對中繼資料的記憶體中更新。</span><span class="sxs-lookup"><span data-stu-id="5d498-104">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d498-105">語法</span><span class="sxs-lookup"><span data-stu-id="5d498-105">Syntax</span></span>  
  
```cpp
typedef enum WriteableMetadataUpdateMode {  
   LegacyCompatPolicy,  
   AlwaysShowUpdates  
} WriteableMetadataUpdateMode;  
```  
  
## <a name="members"></a><span data-ttu-id="5d498-106">成員</span><span class="sxs-lookup"><span data-stu-id="5d498-106">Members</span></span>  
  
|<span data-ttu-id="5d498-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="5d498-107">Member name</span></span>|<span data-ttu-id="5d498-108">描述</span><span class="sxs-lookup"><span data-stu-id="5d498-108">Description</span></span>|  
|-----------------|-----------------|  
|`LegacyCompatPolicy`|<span data-ttu-id="5d498-109">在對中繼資料可見性進行記憶體中更新時，維護與舊版 .NET Framework 的相容性。</span><span class="sxs-lookup"><span data-stu-id="5d498-109">Maintain compatibility with previous versions of the .NET Framework when making in-memory updates to metadata visible.</span></span> <span data-ttu-id="5d498-110">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="5d498-110">See the Remarks section for more information.</span></span>|  
|`AlwaysShowUpdates`|<span data-ttu-id="5d498-111">針對可讓偵錯工具看見的中繼資料進行記憶體中更新。</span><span class="sxs-lookup"><span data-stu-id="5d498-111">Make in-memory updates to metadata visible to the debugger.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d498-112">備註</span><span class="sxs-lookup"><span data-stu-id="5d498-112">Remarks</span></span>  
 <span data-ttu-id="5d498-113">成員`WriteableMetadataUpdateMode`列舉型別可以傳遞至[SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)方法來控制記憶體中是否更新目標處理序中的中繼資料會顯示偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5d498-113">A member of the `WriteableMetadataUpdateMode` enumeration can be passed to the [SetWriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) method to control whether in-memory updates to metadata in the target process are visible to the debugger.</span></span>  
  
 <span data-ttu-id="5d498-114">`LegacyCompatPolicy` 選項會強制執行與 .NET Framework 4.5.2 之前版本中相同的行為。</span><span class="sxs-lookup"><span data-stu-id="5d498-114">The `LegacyCompatPolicy` option enforces the same behavior as in versions of the .NET Framework before 4.5.2.</span></span> <span data-ttu-id="5d498-115">這通常就表示看不到更新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5d498-115">This often means that metadata from updates is not visible.</span></span> <span data-ttu-id="5d498-116">不過，呼叫數個偵錯方法會將偵錯工具隱含強制轉型為可看見更新。</span><span class="sxs-lookup"><span data-stu-id="5d498-116">However, calls to a number of debugging methods implicitly coerce the debugger to make updates visible.</span></span> <span data-ttu-id="5d498-117">例如，如果偵錯工具會傳遞[icordebugilframe:: Getlocalvariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)中找不到方法的原始中繼資料，所有中繼資料的模組更新為 比對的目前狀態的快照集的變數索引程序。</span><span class="sxs-lookup"><span data-stu-id="5d498-117">For example, if the debugger passes [ICorDebugILFrame::GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) the index of a variable not found in the method's original metadata, all metadata for the module is updated to a snapshot matching the current state of the process.</span></span> <span data-ttu-id="5d498-118">換句話說，若使用 `LegacyCompatPolicy` 選項，偵錯工具可能看不到、看到部分或所有可用的中繼資料更新，取決於其使用 Unmanaged 偵錯 API 其他部分的方式。</span><span class="sxs-lookup"><span data-stu-id="5d498-118">In other words, with the `LegacyCompatPolicy` option, the debugger might see none, some, or all of the available metadata updates, depending on how it uses other parts of the unmanaged debugging API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d498-119">需求</span><span class="sxs-lookup"><span data-stu-id="5d498-119">Requirements</span></span>  
 <span data-ttu-id="5d498-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d498-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d498-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d498-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d498-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d498-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d498-123">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d498-123">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d498-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d498-124">See also</span></span>

- [<span data-ttu-id="5d498-125">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5d498-125">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="5d498-126">SetWriteableMetadataUpdateMode 方法</span><span class="sxs-lookup"><span data-stu-id="5d498-126">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)

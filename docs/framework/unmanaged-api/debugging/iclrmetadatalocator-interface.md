---
title: "ICLRMetadataLocator 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a06997c47a85ced56dc579759192f7256def4f5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="e0a64-102">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="e0a64-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="e0a64-103">資料存取服務層用來找出目標處理序中的組件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e0a64-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0a64-104">方法</span><span class="sxs-lookup"><span data-stu-id="e0a64-104">Methods</span></span>  
  
|<span data-ttu-id="e0a64-105">方法</span><span class="sxs-lookup"><span data-stu-id="e0a64-105">Method</span></span>|<span data-ttu-id="e0a64-106">描述</span><span class="sxs-lookup"><span data-stu-id="e0a64-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0a64-107">GetMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="e0a64-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="e0a64-108">從目標處理序中擷取映像的中繼的資料。</span><span class="sxs-lookup"><span data-stu-id="e0a64-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0a64-109">備註</span><span class="sxs-lookup"><span data-stu-id="e0a64-109">Remarks</span></span>  
 <span data-ttu-id="e0a64-110">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="e0a64-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="e0a64-111">例如，即時處理序的實作會是不同的記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="e0a64-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0a64-112">需求</span><span class="sxs-lookup"><span data-stu-id="e0a64-112">Requirements</span></span>  
 <span data-ttu-id="e0a64-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0a64-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a64-114">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e0a64-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e0a64-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0a64-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0a64-116">**.**</span><span class="sxs-lookup"><span data-stu-id="e0a64-116">**.**</span></span> <span data-ttu-id="e0a64-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a64-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a64-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0a64-118">See Also</span></span>  
 [<span data-ttu-id="e0a64-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e0a64-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

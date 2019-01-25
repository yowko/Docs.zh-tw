---
title: ICLRMetadataLocator 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d1d767de88b239c96cb98130b6ff006e3f75b09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495028"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="108e6-102">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="108e6-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="108e6-103">用來找出目標處理序中的組件的中繼資料的資料存取服務層。</span><span class="sxs-lookup"><span data-stu-id="108e6-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="108e6-104">方法</span><span class="sxs-lookup"><span data-stu-id="108e6-104">Methods</span></span>  
  
|<span data-ttu-id="108e6-105">方法</span><span class="sxs-lookup"><span data-stu-id="108e6-105">Method</span></span>|<span data-ttu-id="108e6-106">描述</span><span class="sxs-lookup"><span data-stu-id="108e6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="108e6-107">GetMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="108e6-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="108e6-108">從目標處理序中擷取映像的中繼的資料。</span><span class="sxs-lookup"><span data-stu-id="108e6-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="108e6-109">備註</span><span class="sxs-lookup"><span data-stu-id="108e6-109">Remarks</span></span>  
 <span data-ttu-id="108e6-110">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="108e6-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="108e6-111">比方說，即時處理序的實作是不同的記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="108e6-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="108e6-112">需求</span><span class="sxs-lookup"><span data-stu-id="108e6-112">Requirements</span></span>  
 <span data-ttu-id="108e6-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="108e6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="108e6-114">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="108e6-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="108e6-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="108e6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="108e6-116">**.**</span><span class="sxs-lookup"><span data-stu-id="108e6-116">**.**</span></span> <span data-ttu-id="108e6-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="108e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108e6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="108e6-118">See also</span></span>
- [<span data-ttu-id="108e6-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="108e6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

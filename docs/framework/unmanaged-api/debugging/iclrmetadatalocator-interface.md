---
title: "ICLRMetadataLocator 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator
helpviewer_keywords: ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 955bd6bffe56a166b4c9c313fcb730ce714bf24b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="53e18-102">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="53e18-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="53e18-103">資料存取服務層用來找出目標處理序中的組件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="53e18-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53e18-104">方法</span><span class="sxs-lookup"><span data-stu-id="53e18-104">Methods</span></span>  
  
|<span data-ttu-id="53e18-105">方法</span><span class="sxs-lookup"><span data-stu-id="53e18-105">Method</span></span>|<span data-ttu-id="53e18-106">說明</span><span class="sxs-lookup"><span data-stu-id="53e18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53e18-107">GetMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="53e18-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="53e18-108">從目標處理序中擷取映像的中繼的資料。</span><span class="sxs-lookup"><span data-stu-id="53e18-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e18-109">備註</span><span class="sxs-lookup"><span data-stu-id="53e18-109">Remarks</span></span>  
 <span data-ttu-id="53e18-110">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="53e18-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="53e18-111">例如，即時處理序的實作會是不同的記憶體傾印。</span><span class="sxs-lookup"><span data-stu-id="53e18-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e18-112">需求</span><span class="sxs-lookup"><span data-stu-id="53e18-112">Requirements</span></span>  
 <span data-ttu-id="53e18-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53e18-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e18-114">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="53e18-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="53e18-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53e18-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53e18-116">**.**</span><span class="sxs-lookup"><span data-stu-id="53e18-116">**.**</span></span> <span data-ttu-id="53e18-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e18-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e18-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53e18-118">See Also</span></span>  
 [<span data-ttu-id="53e18-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="53e18-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: ec92214e33cd1acda8b2702d93deba1f0fb2aaa2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111021"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="5be34-102">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="5be34-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="5be34-103">由資料存取服務層用來尋找目標進程中元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5be34-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5be34-104">方法</span><span class="sxs-lookup"><span data-stu-id="5be34-104">Methods</span></span>  
  
|<span data-ttu-id="5be34-105">方法</span><span class="sxs-lookup"><span data-stu-id="5be34-105">Method</span></span>|<span data-ttu-id="5be34-106">描述</span><span class="sxs-lookup"><span data-stu-id="5be34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5be34-107">GetMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="5be34-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="5be34-108">從目標處理常式抓取影像的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5be34-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5be34-109">備註</span><span class="sxs-lookup"><span data-stu-id="5be34-109">Remarks</span></span>  
 <span data-ttu-id="5be34-110">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="5be34-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="5be34-111">例如，即時進程的執行與記憶體傾印的實作為不同。</span><span class="sxs-lookup"><span data-stu-id="5be34-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5be34-112">需求</span><span class="sxs-lookup"><span data-stu-id="5be34-112">Requirements</span></span>  
 <span data-ttu-id="5be34-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5be34-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5be34-114">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="5be34-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5be34-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5be34-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5be34-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5be34-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5be34-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="5be34-117">See also</span></span>

- [<span data-ttu-id="5be34-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5be34-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

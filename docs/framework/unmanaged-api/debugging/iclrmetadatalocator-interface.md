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
ms.openlocfilehash: 69c52c13a4a0aca5094274de969ebed6e09651b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723502"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="d3b5a-102">ICLRMetadataLocator 介面</span><span class="sxs-lookup"><span data-stu-id="d3b5a-102">ICLRMetadataLocator Interface</span></span>

<span data-ttu-id="d3b5a-103">供資料存取服務層用來尋找目標進程中的元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d3b5a-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3b5a-104">方法</span><span class="sxs-lookup"><span data-stu-id="d3b5a-104">Methods</span></span>  
  
|<span data-ttu-id="d3b5a-105">方法</span><span class="sxs-lookup"><span data-stu-id="d3b5a-105">Method</span></span>|<span data-ttu-id="d3b5a-106">描述</span><span class="sxs-lookup"><span data-stu-id="d3b5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3b5a-107">GetMetadata 方法</span><span class="sxs-lookup"><span data-stu-id="d3b5a-107">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="d3b5a-108">從目標進程抓取影像的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="d3b5a-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3b5a-109">備註</span><span class="sxs-lookup"><span data-stu-id="d3b5a-109">Remarks</span></span>  

 <span data-ttu-id="d3b5a-110">API 用戶端 (也就是偵錯工具) 必須針對適合的特定目標處理序實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="d3b5a-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="d3b5a-111">例如，即時進程的執行與記憶體傾印不同。</span><span class="sxs-lookup"><span data-stu-id="d3b5a-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3b5a-112">需求</span><span class="sxs-lookup"><span data-stu-id="d3b5a-112">Requirements</span></span>  

 <span data-ttu-id="d3b5a-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3b5a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b5a-114">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="d3b5a-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d3b5a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3b5a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3b5a-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3b5a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b5a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3b5a-117">See also</span></span>

- [<span data-ttu-id="d3b5a-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d3b5a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

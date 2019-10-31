---
title: ICorPublishProcess 介面
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
ms.openlocfilehash: 04f6a088c5bbe96e3909ba600aa8ffab937abe2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140396"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="060f5-102">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="060f5-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="060f5-103">提供方法，以存取要顯示的處理常式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="060f5-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="060f5-104">方法</span><span class="sxs-lookup"><span data-stu-id="060f5-104">Methods</span></span>  
  
|<span data-ttu-id="060f5-105">方法</span><span class="sxs-lookup"><span data-stu-id="060f5-105">Method</span></span>|<span data-ttu-id="060f5-106">描述</span><span class="sxs-lookup"><span data-stu-id="060f5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="060f5-107">EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="060f5-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="060f5-108">取得[ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)實例，其中包含此 `ICorPublishProcess`所參考之進程中的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="060f5-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="060f5-109">GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="060f5-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="060f5-110">取得此 `ICorPublishProcess`所參考之進程的可執行檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="060f5-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="060f5-111">GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="060f5-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="060f5-112">取得此 `ICorPublishProcess`所參考之進程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="060f5-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="060f5-113">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="060f5-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="060f5-114">取得值，指出此 `ICorPublishProcess` 所參考的進程是否已知執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="060f5-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="060f5-115">需求</span><span class="sxs-lookup"><span data-stu-id="060f5-115">Requirements</span></span>  
 <span data-ttu-id="060f5-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="060f5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="060f5-117">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="060f5-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="060f5-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="060f5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="060f5-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="060f5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060f5-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="060f5-120">See also</span></span>

- [<span data-ttu-id="060f5-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="060f5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="060f5-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="060f5-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)

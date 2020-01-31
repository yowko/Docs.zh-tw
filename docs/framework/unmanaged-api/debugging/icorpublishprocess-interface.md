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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790548"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="d37f6-102">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="d37f6-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="d37f6-103">提供方法，以存取要顯示的處理常式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d37f6-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d37f6-104">方法</span><span class="sxs-lookup"><span data-stu-id="d37f6-104">Methods</span></span>  
  
|<span data-ttu-id="d37f6-105">方法</span><span class="sxs-lookup"><span data-stu-id="d37f6-105">Method</span></span>|<span data-ttu-id="d37f6-106">描述</span><span class="sxs-lookup"><span data-stu-id="d37f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d37f6-107">EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="d37f6-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="d37f6-108">取得[ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)實例，其中包含此 `ICorPublishProcess`所參考之進程中的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="d37f6-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="d37f6-109">GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="d37f6-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="d37f6-110">取得此 `ICorPublishProcess`所參考之進程的可執行檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="d37f6-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="d37f6-111">GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="d37f6-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="d37f6-112">取得此 `ICorPublishProcess`所參考之進程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="d37f6-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="d37f6-113">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="d37f6-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="d37f6-114">取得值，指出此 `ICorPublishProcess` 所參考的進程是否已知執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d37f6-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d37f6-115">需求</span><span class="sxs-lookup"><span data-stu-id="d37f6-115">Requirements</span></span>  
 <span data-ttu-id="d37f6-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d37f6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d37f6-117">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="d37f6-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d37f6-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d37f6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d37f6-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d37f6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37f6-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="d37f6-120">See also</span></span>

- [<span data-ttu-id="d37f6-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d37f6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d37f6-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="d37f6-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)

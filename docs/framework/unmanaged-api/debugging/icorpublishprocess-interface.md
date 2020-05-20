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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421081"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="32bcf-102">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="32bcf-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="32bcf-103">提供方法，以存取要顯示的處理常式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="32bcf-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32bcf-104">方法</span><span class="sxs-lookup"><span data-stu-id="32bcf-104">Methods</span></span>  
  
|<span data-ttu-id="32bcf-105">方法</span><span class="sxs-lookup"><span data-stu-id="32bcf-105">Method</span></span>|<span data-ttu-id="32bcf-106">描述</span><span class="sxs-lookup"><span data-stu-id="32bcf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32bcf-107">EnumAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="32bcf-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="32bcf-108">取得[ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)實例，其中包含這個所參考之進程中的應用程式域 `ICorPublishProcess` 。</span><span class="sxs-lookup"><span data-stu-id="32bcf-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="32bcf-109">GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="32bcf-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="32bcf-110">取得這個所參考之進程的可執行檔完整路徑 `ICorPublishProcess` 。</span><span class="sxs-lookup"><span data-stu-id="32bcf-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="32bcf-111">GetProcessID 方法</span><span class="sxs-lookup"><span data-stu-id="32bcf-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="32bcf-112">取得這個所參考之進程的作業系統識別碼 `ICorPublishProcess` 。</span><span class="sxs-lookup"><span data-stu-id="32bcf-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="32bcf-113">IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="32bcf-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="32bcf-114">取得值，指出這個所參考的進程是否 `ICorPublishProcess` 已知正在執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="32bcf-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32bcf-115">需求</span><span class="sxs-lookup"><span data-stu-id="32bcf-115">Requirements</span></span>  
 <span data-ttu-id="32bcf-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32bcf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32bcf-117">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="32bcf-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="32bcf-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32bcf-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32bcf-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32bcf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bcf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32bcf-120">See also</span></span>

- [<span data-ttu-id="32bcf-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="32bcf-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="32bcf-122">CorpubPublish Coclass</span><span class="sxs-lookup"><span data-stu-id="32bcf-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)

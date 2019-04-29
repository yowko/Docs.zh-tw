---
title: IAssemblyCache 介面
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fc5f3a3d5bc5699a596bcc648a7153190c130f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697676"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="6425a-102">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="6425a-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="6425a-103">表示使用的全域組件快取融合技術。</span><span class="sxs-lookup"><span data-stu-id="6425a-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6425a-104">方法</span><span class="sxs-lookup"><span data-stu-id="6425a-104">Methods</span></span>  
  
|<span data-ttu-id="6425a-105">方法</span><span class="sxs-lookup"><span data-stu-id="6425a-105">Method</span></span>|<span data-ttu-id="6425a-106">描述</span><span class="sxs-lookup"><span data-stu-id="6425a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6425a-107">CreateAssemblyCacheItem 方法</span><span class="sxs-lookup"><span data-stu-id="6425a-107">CreateAssemblyCacheItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="6425a-108">取得新的參考[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6425a-108">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="6425a-109">CreateAssemblyScavenger 方法</span><span class="sxs-lookup"><span data-stu-id="6425a-109">CreateAssemblyScavenger Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="6425a-110">融合技術，以保留供內部使用。</span><span class="sxs-lookup"><span data-stu-id="6425a-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="6425a-111">InstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="6425a-111">InstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-installassembly-method.md)|<span data-ttu-id="6425a-112">指定的組件安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="6425a-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="6425a-113">QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="6425a-113">QueryAssemblyInfo Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="6425a-114">取得指定的組件的相關要求的資料。</span><span class="sxs-lookup"><span data-stu-id="6425a-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="6425a-115">UninstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="6425a-115">UninstallAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="6425a-116">從全域組件快取，解除安裝指定的組件。</span><span class="sxs-lookup"><span data-stu-id="6425a-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6425a-117">需求</span><span class="sxs-lookup"><span data-stu-id="6425a-117">Requirements</span></span>  
 <span data-ttu-id="6425a-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6425a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6425a-119">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6425a-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6425a-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6425a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6425a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6425a-121">See also</span></span>

- [<span data-ttu-id="6425a-122">融合介面</span><span class="sxs-lookup"><span data-stu-id="6425a-122">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="6425a-123">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="6425a-123">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)

---
title: "IAssemblyCache::UninstallAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.UninstallAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d34b2793de58721c7d4863855106d4b231bccc54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="691e6-102">IAssemblyCache::UninstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="691e6-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="691e6-103">解除安裝指定的組件，從全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="691e6-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="691e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="691e6-104">Syntax</span></span>  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="691e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="691e6-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="691e6-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="691e6-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="691e6-107">[in]若要解除安裝組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="691e6-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="691e6-108">[in]A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)包含組件之安裝資料的結構。</span><span class="sxs-lookup"><span data-stu-id="691e6-108">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="691e6-109">[out，optional]其中包括下列： 配置值。</span><span class="sxs-lookup"><span data-stu-id="691e6-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="691e6-110">可能的值包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="691e6-110">Possible values include the following:</span></span>  
  
-   <span data-ttu-id="691e6-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="691e6-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
-   <span data-ttu-id="691e6-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="691e6-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
-   <span data-ttu-id="691e6-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="691e6-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
-   <span data-ttu-id="691e6-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="691e6-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
-   <span data-ttu-id="691e6-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="691e6-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
-   <span data-ttu-id="691e6-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="691e6-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="691e6-117">需求</span><span class="sxs-lookup"><span data-stu-id="691e6-117">Requirements</span></span>  
 <span data-ttu-id="691e6-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="691e6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="691e6-119">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="691e6-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="691e6-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="691e6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691e6-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="691e6-121">See Also</span></span>  
 [<span data-ttu-id="691e6-122">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="691e6-122">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)

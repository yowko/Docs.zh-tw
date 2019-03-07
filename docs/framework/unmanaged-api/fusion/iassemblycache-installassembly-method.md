---
title: IAssemblyCache::InstallAssembly 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50152b72cade763a5b890c0c9d45109d88ce65a7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469205"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="b9acd-102">IAssemblyCache::InstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="b9acd-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="b9acd-103">指定的組件安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="b9acd-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9acd-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9acd-104">Syntax</span></span>  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9acd-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9acd-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b9acd-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="b9acd-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="b9acd-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="b9acd-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="b9acd-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="b9acd-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="b9acd-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="b9acd-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="b9acd-110">[in]若要安裝組件資訊清單的路徑。</span><span class="sxs-lookup"><span data-stu-id="b9acd-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="b9acd-111">[in]A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)包含安裝的資料結構。</span><span class="sxs-lookup"><span data-stu-id="b9acd-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9acd-112">需求</span><span class="sxs-lookup"><span data-stu-id="b9acd-112">Requirements</span></span>  
 <span data-ttu-id="b9acd-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9acd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9acd-114">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b9acd-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b9acd-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9acd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9acd-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9acd-116">See also</span></span>
- [<span data-ttu-id="b9acd-117">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="b9acd-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)

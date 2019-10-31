---
title: IAssemblyCache::UninstallAssembly 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
ms.openlocfilehash: 539a8edf6d7248235a6e672edc9464679a2eab82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134504"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="51e9b-102">IAssemblyCache::UninstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="51e9b-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="51e9b-103">從全域組件快取卸載指定的元件。</span><span class="sxs-lookup"><span data-stu-id="51e9b-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51e9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="51e9b-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51e9b-105">參數</span><span class="sxs-lookup"><span data-stu-id="51e9b-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="51e9b-106">在在融合 .idl 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="51e9b-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="51e9b-107">在要卸載之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="51e9b-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="51e9b-108">在包含元件之安裝資料的[FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="51e9b-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="51e9b-109">[out，optional]在融合 .idl 中定義的其中一個配置值。</span><span class="sxs-lookup"><span data-stu-id="51e9b-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="51e9b-110">可能的值包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="51e9b-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="51e9b-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED （1）</span><span class="sxs-lookup"><span data-stu-id="51e9b-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="51e9b-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE （2）</span><span class="sxs-lookup"><span data-stu-id="51e9b-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="51e9b-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED （3）</span><span class="sxs-lookup"><span data-stu-id="51e9b-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="51e9b-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING （4）</span><span class="sxs-lookup"><span data-stu-id="51e9b-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="51e9b-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES （5）</span><span class="sxs-lookup"><span data-stu-id="51e9b-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="51e9b-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND （6）</span><span class="sxs-lookup"><span data-stu-id="51e9b-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51e9b-117">需求</span><span class="sxs-lookup"><span data-stu-id="51e9b-117">Requirements</span></span>  
 <span data-ttu-id="51e9b-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51e9b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51e9b-119">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="51e9b-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="51e9b-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51e9b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51e9b-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="51e9b-121">See also</span></span>

- [<span data-ttu-id="51e9b-122">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="51e9b-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)

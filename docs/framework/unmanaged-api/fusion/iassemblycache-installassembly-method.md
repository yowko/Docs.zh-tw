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
ms.openlocfilehash: 230b904dd1cca1a1289713e3df7a709bd1c3a22b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696878"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="0d733-102">IAssemblyCache::InstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="0d733-102">IAssemblyCache::InstallAssembly Method</span></span>

<span data-ttu-id="0d733-103">在全域組件快取中安裝指定的元件。</span><span class="sxs-lookup"><span data-stu-id="0d733-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d733-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d733-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d733-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d733-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="0d733-106">在在融合 .idl 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="0d733-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="0d733-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="0d733-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="0d733-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001) </span><span class="sxs-lookup"><span data-stu-id="0d733-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="0d733-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002) </span><span class="sxs-lookup"><span data-stu-id="0d733-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="0d733-110">在要安裝之元件的資訊清單路徑。</span><span class="sxs-lookup"><span data-stu-id="0d733-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="0d733-111">在包含安裝資料的 [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) 結構。</span><span class="sxs-lookup"><span data-stu-id="0d733-111">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d733-112">需求</span><span class="sxs-lookup"><span data-stu-id="0d733-112">Requirements</span></span>  

 <span data-ttu-id="0d733-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d733-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d733-114">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="0d733-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0d733-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d733-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d733-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d733-116">See also</span></span>

- [<span data-ttu-id="0d733-117">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="0d733-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)

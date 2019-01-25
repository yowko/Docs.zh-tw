---
title: IAssemblyCache::CreateAssemblyCacheItem 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27001f8560dcd128b5d737ed0f219387be86d6e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672301"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="ea0f2-102">IAssemblyCache::CreateAssemblyCacheItem 方法</span><span class="sxs-lookup"><span data-stu-id="ea0f2-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="ea0f2-103">取得新的參考[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="ea0f2-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea0f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea0f2-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea0f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea0f2-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="ea0f2-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="ea0f2-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="ea0f2-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="ea0f2-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="ea0f2-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="ea0f2-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="ea0f2-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="ea0f2-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ea0f2-110">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="ea0f2-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ea0f2-111">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="ea0f2-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="ea0f2-112">[out]傳回`IAssemblyCacheItem`指標。</span><span class="sxs-lookup"><span data-stu-id="ea0f2-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="ea0f2-113">[in，選用]Uncanonicalized 的逗點分隔`name=value`組。</span><span class="sxs-lookup"><span data-stu-id="ea0f2-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea0f2-114">需求</span><span class="sxs-lookup"><span data-stu-id="ea0f2-114">Requirements</span></span>  
 <span data-ttu-id="ea0f2-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea0f2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea0f2-116">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ea0f2-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ea0f2-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea0f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea0f2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea0f2-118">See also</span></span>
- [<span data-ttu-id="ea0f2-119">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="ea0f2-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="ea0f2-120">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="ea0f2-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)

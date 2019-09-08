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
ms.openlocfilehash: 215eb3a508a746230d36fdda3e8ba992287be62c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796824"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="bae27-102">IAssemblyCache::CreateAssemblyCacheItem 方法</span><span class="sxs-lookup"><span data-stu-id="bae27-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="bae27-103">取得新[IAssemblyCacheItem](iassemblycacheitem-interface.md)物件的參考。</span><span class="sxs-lookup"><span data-stu-id="bae27-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bae27-104">語法</span><span class="sxs-lookup"><span data-stu-id="bae27-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bae27-105">參數</span><span class="sxs-lookup"><span data-stu-id="bae27-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="bae27-106">在在融合 .idl 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="bae27-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="bae27-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="bae27-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="bae27-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH （0x00000001）</span><span class="sxs-lookup"><span data-stu-id="bae27-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="bae27-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH （0x00000002）</span><span class="sxs-lookup"><span data-stu-id="bae27-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="bae27-110">在保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="bae27-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="bae27-111">`pvReserved`必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="bae27-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="bae27-112">脫銷傳回`IAssemblyCacheItem`的指標。</span><span class="sxs-lookup"><span data-stu-id="bae27-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="bae27-113">[in，optional]Uncanonicalized，以逗號分隔`name=value`的配對。</span><span class="sxs-lookup"><span data-stu-id="bae27-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bae27-114">需求</span><span class="sxs-lookup"><span data-stu-id="bae27-114">Requirements</span></span>  
 <span data-ttu-id="bae27-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bae27-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bae27-116">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="bae27-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bae27-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bae27-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bae27-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bae27-118">See also</span></span>

- [<span data-ttu-id="bae27-119">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="bae27-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="bae27-120">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="bae27-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)

---
title: ICeeGen::AddSectionReloc 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e74d625cadb2febe45aa4c000e5b63f96aada55
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494099"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="90b93-102">ICeeGen::AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="90b93-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="90b93-103">將程式碼基底.reloc 指令。</span><span class="sxs-lookup"><span data-stu-id="90b93-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="90b93-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="90b93-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90b93-105">語法</span><span class="sxs-lookup"><span data-stu-id="90b93-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90b93-106">參數</span><span class="sxs-lookup"><span data-stu-id="90b93-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="90b93-107">[in]要加入.reloc 指令的記憶體中程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="90b93-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="90b93-108">[in]此區段的位移。</span><span class="sxs-lookup"><span data-stu-id="90b93-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="90b93-109">[in]這一節`offset`參考。</span><span class="sxs-lookup"><span data-stu-id="90b93-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="90b93-110">[in]其中一個[CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)值，表示將.reloc 指令的類型。</span><span class="sxs-lookup"><span data-stu-id="90b93-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90b93-111">需求</span><span class="sxs-lookup"><span data-stu-id="90b93-111">Requirements</span></span>  
 <span data-ttu-id="90b93-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90b93-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90b93-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="90b93-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90b93-114">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="90b93-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90b93-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90b93-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b93-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90b93-116">See also</span></span>
- [<span data-ttu-id="90b93-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="90b93-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

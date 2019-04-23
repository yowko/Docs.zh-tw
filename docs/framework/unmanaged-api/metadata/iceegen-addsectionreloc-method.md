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
ms.openlocfilehash: 7d50f7488c2b231ea66c12cc4903469d9e2337fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088375"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="68e90-102">ICeeGen::AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="68e90-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="68e90-103">將程式碼基底.reloc 指令。</span><span class="sxs-lookup"><span data-stu-id="68e90-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="68e90-104">這個方法已經過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="68e90-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e90-105">語法</span><span class="sxs-lookup"><span data-stu-id="68e90-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68e90-106">參數</span><span class="sxs-lookup"><span data-stu-id="68e90-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="68e90-107">[in]要加入.reloc 指令的記憶體中程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="68e90-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="68e90-108">[in]此區段的位移。</span><span class="sxs-lookup"><span data-stu-id="68e90-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="68e90-109">[in]這一節`offset`參考。</span><span class="sxs-lookup"><span data-stu-id="68e90-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="68e90-110">[in]其中一個[CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)值，表示將.reloc 指令的類型。</span><span class="sxs-lookup"><span data-stu-id="68e90-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e90-111">需求</span><span class="sxs-lookup"><span data-stu-id="68e90-111">Requirements</span></span>  
 <span data-ttu-id="68e90-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68e90-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e90-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="68e90-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68e90-114">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="68e90-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68e90-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e90-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e90-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68e90-116">See also</span></span>

- [<span data-ttu-id="68e90-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="68e90-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

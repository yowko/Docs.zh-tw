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
ms.openlocfilehash: e5940f229e86b46bb8c5d5b2f9920a8261359f65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436417"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="aa51b-102">ICeeGen::AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="aa51b-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="aa51b-103">將 reloc 指令新增至程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="aa51b-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="aa51b-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="aa51b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa51b-105">語法</span><span class="sxs-lookup"><span data-stu-id="aa51b-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa51b-106">參數</span><span class="sxs-lookup"><span data-stu-id="aa51b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="aa51b-107">在要加入 reloc 指令的記憶體內部程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="aa51b-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="aa51b-108">在區段的位移。</span><span class="sxs-lookup"><span data-stu-id="aa51b-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="aa51b-109">在`offset` 所參考的區段。</span><span class="sxs-lookup"><span data-stu-id="aa51b-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="aa51b-110">在其中一個[CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)值，表示要新增的 reloc 指令類型。</span><span class="sxs-lookup"><span data-stu-id="aa51b-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa51b-111">需求</span><span class="sxs-lookup"><span data-stu-id="aa51b-111">Requirements</span></span>  
 <span data-ttu-id="aa51b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aa51b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa51b-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="aa51b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa51b-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="aa51b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa51b-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa51b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa51b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa51b-116">See also</span></span>

- [<span data-ttu-id="aa51b-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="aa51b-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

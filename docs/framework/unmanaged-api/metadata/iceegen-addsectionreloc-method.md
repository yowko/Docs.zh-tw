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
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176106"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="fc9d7-102">ICeeGen::AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="fc9d7-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="fc9d7-103">向代碼庫添加 .reloc 指令。</span><span class="sxs-lookup"><span data-stu-id="fc9d7-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="fc9d7-104">此方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="fc9d7-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc9d7-105">語法</span><span class="sxs-lookup"><span data-stu-id="fc9d7-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc9d7-106">參數</span><span class="sxs-lookup"><span data-stu-id="fc9d7-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="fc9d7-107">[在]要向其添加 .reloc 指令的記憶體代碼部分。</span><span class="sxs-lookup"><span data-stu-id="fc9d7-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="fc9d7-108">[在]節的偏移量。</span><span class="sxs-lookup"><span data-stu-id="fc9d7-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="fc9d7-109">[在]引用的`offset`節。</span><span class="sxs-lookup"><span data-stu-id="fc9d7-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="fc9d7-110">[在][CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)值之一，指示要添加的 .reloc 指令的類型。</span><span class="sxs-lookup"><span data-stu-id="fc9d7-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc9d7-111">需求</span><span class="sxs-lookup"><span data-stu-id="fc9d7-111">Requirements</span></span>  
 <span data-ttu-id="fc9d7-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc9d7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc9d7-113">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="fc9d7-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc9d7-114">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fc9d7-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc9d7-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc9d7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9d7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc9d7-116">See also</span></span>

- [<span data-ttu-id="fc9d7-117">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="fc9d7-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

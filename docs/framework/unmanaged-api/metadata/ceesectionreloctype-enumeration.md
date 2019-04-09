---
title: CeeSectionRelocType 列舉
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882242da493c49a2e6aa09888e9503dcf2933589
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119583"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="ca144-102">CeeSectionRelocType 列舉</span><span class="sxs-lookup"><span data-stu-id="ca144-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="ca144-103">提供值，以影響的型別`reloc`發出的呼叫中的指示[iceegen:: Addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ca144-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca144-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca144-104">Syntax</span></span>  
  
```  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="ca144-105">成員</span><span class="sxs-lookup"><span data-stu-id="ca144-105">Members</span></span>  
  
|<span data-ttu-id="ca144-106">成員</span><span class="sxs-lookup"><span data-stu-id="ca144-106">Member</span></span>|<span data-ttu-id="ca144-107">描述</span><span class="sxs-lookup"><span data-stu-id="ca144-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="ca144-108">產生僅區段相對`reloc`、 傳送任何項目到.reloc 區段。</span><span class="sxs-lookup"><span data-stu-id="ca144-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="ca144-109">會產生`reloc`指標大小的位置。</span><span class="sxs-lookup"><span data-stu-id="ca144-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="ca144-110">這會轉換成 BASED_HIGHLOW 或 BASED_DIR64 視平台。</span><span class="sxs-lookup"><span data-stu-id="ca144-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="ca144-111">會產生`reloc`前 32 位元數字，其中 16 位元會包含在下一個字.reloc 資料表中的 16 位元。</span><span class="sxs-lookup"><span data-stu-id="ca144-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="ca144-112">會產生語彙基元對應的重新配置，傳送任何項目到.reloc 區段。</span><span class="sxs-lookup"><span data-stu-id="ca144-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="ca144-113">表示值是相對位址的修復。</span><span class="sxs-lookup"><span data-stu-id="ca144-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="ca144-114">產生僅區段相對`reloc`、 傳送任何項目到.reloc 區段。</span><span class="sxs-lookup"><span data-stu-id="ca144-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="ca144-115">這`reloc`是檔案的相對位置 區段中，不該區段的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="ca144-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="ca144-116">指定程式碼的相對位址的修復。</span><span class="sxs-lookup"><span data-stu-id="ca144-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="ca144-117">會產生`reloc`64 位元位址在 ia64`movl`指令。</span><span class="sxs-lookup"><span data-stu-id="ca144-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="ca144-118">會產生`reloc`64 位元位址。</span><span class="sxs-lookup"><span data-stu-id="ca144-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="ca144-119">產生`reloc`25 位元電腦相對位址在 ia64`br.call`指令。</span><span class="sxs-lookup"><span data-stu-id="ca144-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="ca144-120">會產生`reloc`64 位元電腦相對位址在 ia64`brl.call`指令。</span><span class="sxs-lookup"><span data-stu-id="ca144-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="ca144-121">會產生 30 位元的區段相對於`reloc`，用來標記的指標值。</span><span class="sxs-lookup"><span data-stu-id="ca144-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="ca144-122">為了協助確保這個列舉任何新增項目之 sentinel 值會反映到內部`reloc`名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="ca144-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="ca144-123">指定不要發出基底`reloc`。</span><span class="sxs-lookup"><span data-stu-id="ca144-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="ca144-124">值，指出前修復記憶體內容的指標，而不是區段位移。</span><span class="sxs-lookup"><span data-stu-id="ca144-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca144-125">需求</span><span class="sxs-lookup"><span data-stu-id="ca144-125">Requirements</span></span>  
 <span data-ttu-id="ca144-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca144-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca144-127">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ca144-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca144-128">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ca144-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ca144-129">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ca144-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ca144-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca144-130">See also</span></span>

- [<span data-ttu-id="ca144-131">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="ca144-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="ca144-132">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="ca144-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="ca144-133">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="ca144-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)

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
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176210"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="83f39-102">CeeSectionRelocType 列舉</span><span class="sxs-lookup"><span data-stu-id="83f39-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="83f39-103">提供值以影響調用 ICeeGen 時發出的`reloc`指令類型[：：AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)。</span><span class="sxs-lookup"><span data-stu-id="83f39-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f39-104">語法</span><span class="sxs-lookup"><span data-stu-id="83f39-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="83f39-105">成員</span><span class="sxs-lookup"><span data-stu-id="83f39-105">Members</span></span>  
  
|<span data-ttu-id="83f39-106">member</span><span class="sxs-lookup"><span data-stu-id="83f39-106">Member</span></span>|<span data-ttu-id="83f39-107">描述</span><span class="sxs-lookup"><span data-stu-id="83f39-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="83f39-108">僅生成與節相關的`reloc`，不會將任何內容發送到 .reloc 節。</span><span class="sxs-lookup"><span data-stu-id="83f39-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="83f39-109">為指標`reloc`大小的位置生成 。</span><span class="sxs-lookup"><span data-stu-id="83f39-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="83f39-110">根據平臺的不同，這轉換為BASED_HIGHLOW或BASED_DIR64。</span><span class="sxs-lookup"><span data-stu-id="83f39-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="83f39-111">為`reloc`32 位數位的前 16 位生成 一個，其中底部 16 位包含在 .reloc 表中的下一個單詞中。</span><span class="sxs-lookup"><span data-stu-id="83f39-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="83f39-112">生成權杖映射重新置放，不向 .reloc 部分發送任何內容。</span><span class="sxs-lookup"><span data-stu-id="83f39-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="83f39-113">指示該值是相對位址修復。</span><span class="sxs-lookup"><span data-stu-id="83f39-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="83f39-114">僅生成與節相關的`reloc`，不會將任何內容發送到 .reloc 節。</span><span class="sxs-lookup"><span data-stu-id="83f39-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="83f39-115">這是`reloc`相對於節的檔位置，而不是節的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="83f39-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="83f39-116">指定與代碼相關的位址修復。</span><span class="sxs-lookup"><span data-stu-id="83f39-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="83f39-117">在`reloc`ia64 指令中為 64`movl`位位址生成 。</span><span class="sxs-lookup"><span data-stu-id="83f39-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="83f39-118">為`reloc`64 位位址生成 。</span><span class="sxs-lookup"><span data-stu-id="83f39-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="83f39-119">在`reloc`ia64`br.call`指令中為 25 位 PC 相關位址生成 。</span><span class="sxs-lookup"><span data-stu-id="83f39-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="83f39-120">在`reloc`ia64`brl.call`指令中為 64 位 PC 相關位址生成 。</span><span class="sxs-lookup"><span data-stu-id="83f39-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="83f39-121">生成 30 位節相對`reloc`， 用於標記的指標值。</span><span class="sxs-lookup"><span data-stu-id="83f39-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="83f39-122">一個哨點值，可説明確保此枚舉的任何添加都反映到內部`reloc`名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="83f39-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="83f39-123">指定不發出基`reloc`。</span><span class="sxs-lookup"><span data-stu-id="83f39-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="83f39-124">指示記憶體的預修復內容是指標而不是節偏移量的值。</span><span class="sxs-lookup"><span data-stu-id="83f39-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83f39-125">需求</span><span class="sxs-lookup"><span data-stu-id="83f39-125">Requirements</span></span>  
 <span data-ttu-id="83f39-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83f39-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f39-127">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="83f39-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83f39-128">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="83f39-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83f39-129">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f39-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f39-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83f39-130">See also</span></span>

- [<span data-ttu-id="83f39-131">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="83f39-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="83f39-132">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="83f39-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="83f39-133">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="83f39-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)

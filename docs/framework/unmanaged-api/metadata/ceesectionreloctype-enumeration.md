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
ms.openlocfilehash: f7aa9699e9929608c90020c6b2d66c301fc11955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732706"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="d7cb8-102">CeeSectionRelocType 列舉</span><span class="sxs-lookup"><span data-stu-id="d7cb8-102">CeeSectionRelocType Enumeration</span></span>

<span data-ttu-id="d7cb8-103">提供值，以影響 `reloc` [ICeeGen：： AddSectionReloc](iceegen-addsectionreloc-method.md)呼叫中發出的指令類型。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7cb8-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7cb8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d7cb8-105">成員</span><span class="sxs-lookup"><span data-stu-id="d7cb8-105">Members</span></span>  
  
|<span data-ttu-id="d7cb8-106">member</span><span class="sxs-lookup"><span data-stu-id="d7cb8-106">Member</span></span>|<span data-ttu-id="d7cb8-107">描述</span><span class="sxs-lookup"><span data-stu-id="d7cb8-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="d7cb8-108">只產生區段相關，不傳送 `reloc` 任何內容至 reloc 區段。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="d7cb8-109">`reloc`針對指標大小位置產生。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="d7cb8-110">這會轉換成 BASED_HIGHLOW 或 BASED_DIR64，視平臺而定。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="d7cb8-111">`reloc`針對32位數位的前16位產生，其中的下16位會包含在 reloc 資料表的下一個單字中。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="d7cb8-112">產生權杖對應重新配置，將 nothing 傳送至 reloc 區段。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="d7cb8-113">指出值是相對位址修復。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="d7cb8-114">只產生區段相關，不傳送 `reloc` 任何內容至 reloc 區段。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="d7cb8-115">這 `reloc` 是相對於區段的檔案位置，而不是區段的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="d7cb8-116">指定與程式碼相關的位址修復。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="d7cb8-117">`reloc`針對 ia64 指令中的64位位址產生 `movl` 。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="d7cb8-118">產生 `reloc` 64 位位址的。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="d7cb8-119">`reloc`在 ia64 指令中為25位的電腦相對位址產生 `br.call` 。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="d7cb8-120">`reloc`針對 ia64 指令中的64位電腦相對位址產生 `brl.call` 。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="d7cb8-121">產生與標記指標值相關的30位區段 `reloc` 。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="d7cb8-122">Sentinel 值，可協助確保此列舉的任何新增專案都會反映在內部 `reloc` 名稱陣列中。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="d7cb8-123">指定不發出基底 `reloc` 。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="d7cb8-124">值，表示記憶體的預先修復內容是指標，而不是區段位移。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7cb8-125">需求</span><span class="sxs-lookup"><span data-stu-id="d7cb8-125">Requirements</span></span>  

 <span data-ttu-id="d7cb8-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7cb8-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7cb8-127">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d7cb8-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7cb8-128">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d7cb8-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d7cb8-129">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7cb8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cb8-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7cb8-130">See also</span></span>

- [<span data-ttu-id="d7cb8-131">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="d7cb8-131">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="d7cb8-132">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="d7cb8-132">ICeeGen Interface</span></span>](iceegen-interface.md)
- [<span data-ttu-id="d7cb8-133">AddSectionReloc 方法</span><span class="sxs-lookup"><span data-stu-id="d7cb8-133">AddSectionReloc Method</span></span>](iceegen-addsectionreloc-method.md)

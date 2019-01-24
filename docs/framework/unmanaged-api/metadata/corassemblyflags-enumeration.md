---
title: CorAssemblyFlags 列舉
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f99fb7a693c47b257abe9c0b783856179fc9f0eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582369"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="db898-102">CorAssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="db898-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="db898-103">包含值，這些值描述套用至組件編譯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="db898-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db898-104">語法</span><span class="sxs-lookup"><span data-stu-id="db898-104">Syntax</span></span>  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="db898-105">成員</span><span class="sxs-lookup"><span data-stu-id="db898-105">Members</span></span>  
  
|<span data-ttu-id="db898-106">成員</span><span class="sxs-lookup"><span data-stu-id="db898-106">Member</span></span>|<span data-ttu-id="db898-107">描述</span><span class="sxs-lookup"><span data-stu-id="db898-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="db898-108">表示組件參考會保留完整的雜湊的公用金鑰。</span><span class="sxs-lookup"><span data-stu-id="db898-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="db898-109">表示未指定的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="db898-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="db898-110">指出處理器架構是中性 (PE32)。</span><span class="sxs-lookup"><span data-stu-id="db898-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="db898-111">指出處理器架構為 x86 (PE32)。</span><span class="sxs-lookup"><span data-stu-id="db898-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="db898-112">指示處理器架構為 Itanium （PE32 +）。</span><span class="sxs-lookup"><span data-stu-id="db898-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="db898-113">指出處理器架構的 AMD X64 （PE32 +）。</span><span class="sxs-lookup"><span data-stu-id="db898-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="db898-114">指出處理器架構是 ARM (PE32)。</span><span class="sxs-lookup"><span data-stu-id="db898-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="db898-115">表示組件的參考組件;也就是它會套用至任何架構，但無法在任何架構上執行。</span><span class="sxs-lookup"><span data-stu-id="db898-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="db898-116">因此，此旗標等同於`afPA_Mask`。</span><span class="sxs-lookup"><span data-stu-id="db898-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="db898-117">指出處理器架構旗標，應該傳播至`AssemblyRef`記錄。</span><span class="sxs-lookup"><span data-stu-id="db898-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="db898-118">遮罩，描述處理器架構。</span><span class="sxs-lookup"><span data-stu-id="db898-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="db898-119">指定包含處理器架構的說明。</span><span class="sxs-lookup"><span data-stu-id="db898-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="db898-120">指出處理器架構旗標，從索引中的移位計數。</span><span class="sxs-lookup"><span data-stu-id="db898-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="db898-121">從對應的值會指出<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。</span><span class="sxs-lookup"><span data-stu-id="db898-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="db898-122">從對應的值會指出<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>的<xref:System.Diagnostics.DebuggableAttribute>。</span><span class="sxs-lookup"><span data-stu-id="db898-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="db898-123">表示組件可以被重定目標在執行階段組件從不同的 「 發行者 」。</span><span class="sxs-lookup"><span data-stu-id="db898-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="db898-124">遮罩，描述的內容類型。</span><span class="sxs-lookup"><span data-stu-id="db898-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="db898-125">表示預設內容類型。</span><span class="sxs-lookup"><span data-stu-id="db898-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="db898-126">指出[!INCLUDE[wrt](../../../../includes/wrt-md.md)]內容類型。</span><span class="sxs-lookup"><span data-stu-id="db898-126">Indicates the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db898-127">需求</span><span class="sxs-lookup"><span data-stu-id="db898-127">Requirements</span></span>  
 <span data-ttu-id="db898-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db898-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db898-129">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="db898-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="db898-130">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db898-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db898-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db898-131">See also</span></span>
- [<span data-ttu-id="db898-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="db898-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

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
ms.openlocfilehash: b1a83f07f03ddb17d5c306453cf838101a77ed65
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007932"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="94177-102">CorAssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="94177-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="94177-103">包含值，這些值描述套用至組件編譯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="94177-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94177-104">語法</span><span class="sxs-lookup"><span data-stu-id="94177-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="94177-105">成員</span><span class="sxs-lookup"><span data-stu-id="94177-105">Members</span></span>  
  
|<span data-ttu-id="94177-106">成員</span><span class="sxs-lookup"><span data-stu-id="94177-106">Member</span></span>|<span data-ttu-id="94177-107">描述</span><span class="sxs-lookup"><span data-stu-id="94177-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="94177-108">表示元件參考包含完整、未經過雜湊的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="94177-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="94177-109">表示未指定處理器架構。</span><span class="sxs-lookup"><span data-stu-id="94177-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="94177-110">表示處理器架構為中性（PE32）。</span><span class="sxs-lookup"><span data-stu-id="94177-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="94177-111">指出處理器架構為 x86 （PE32）。</span><span class="sxs-lookup"><span data-stu-id="94177-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="94177-112">指出處理器架構為 Itanium （PE32 +）。</span><span class="sxs-lookup"><span data-stu-id="94177-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="94177-113">指出處理器架構是 AMD X64 （PE32 +）。</span><span class="sxs-lookup"><span data-stu-id="94177-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="94177-114">指出處理器架構為 ARM （PE32）。</span><span class="sxs-lookup"><span data-stu-id="94177-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="94177-115">表示元件是參考元件;也就是說，它會套用至任何架構，但無法在任何架構上執行。</span><span class="sxs-lookup"><span data-stu-id="94177-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="94177-116">因此，旗標與相同 `afPA_Mask` 。</span><span class="sxs-lookup"><span data-stu-id="94177-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="94177-117">指出處理器架構旗標應該傳播至 `AssemblyRef` 記錄。</span><span class="sxs-lookup"><span data-stu-id="94177-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="94177-118">描述處理器架構的遮罩。</span><span class="sxs-lookup"><span data-stu-id="94177-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="94177-119">指定包含處理器架構的描述。</span><span class="sxs-lookup"><span data-stu-id="94177-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="94177-120">表示在處理器架構旗標中與索引之間的位移計數。</span><span class="sxs-lookup"><span data-stu-id="94177-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="94177-121">表示的對應值 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="94177-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="94177-122">表示的對應值 <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="94177-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="94177-123">表示元件可以在執行時間重定目標，使其成為來自不同發行者的元件。</span><span class="sxs-lookup"><span data-stu-id="94177-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="94177-124">描述內容類型的遮罩。</span><span class="sxs-lookup"><span data-stu-id="94177-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="94177-125">表示預設內容類型。</span><span class="sxs-lookup"><span data-stu-id="94177-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="94177-126">表示 Windows 執行階段內容類型。</span><span class="sxs-lookup"><span data-stu-id="94177-126">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94177-127">需求</span><span class="sxs-lookup"><span data-stu-id="94177-127">Requirements</span></span>  
 <span data-ttu-id="94177-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94177-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94177-129">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="94177-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="94177-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94177-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94177-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94177-131">See also</span></span>

- [<span data-ttu-id="94177-132">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="94177-132">Metadata Enumerations</span></span>](metadata-enumerations.md)

---
title: ASSEMBLY_INFO 結構
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110873"
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="bdf2d-102">ASSEMBLY_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="bdf2d-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="bdf2d-103">包含在全域組件快取中註冊組件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdf2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdf2d-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="bdf2d-105">成員</span><span class="sxs-lookup"><span data-stu-id="bdf2d-105">Members</span></span>  
  
|<span data-ttu-id="bdf2d-106">成員</span><span class="sxs-lookup"><span data-stu-id="bdf2d-106">Member</span></span>|<span data-ttu-id="bdf2d-107">描述</span><span class="sxs-lookup"><span data-stu-id="bdf2d-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="bdf2d-108">以位元組為單位的結構大小。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="bdf2d-109">此欄位保留以供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="bdf2d-110">旗標，表示安裝的組件的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="bdf2d-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="bdf2d-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="bdf2d-112">-ASSEMBLYINFO_FLAG_INSTALLED 」 值，指出已安裝的組件。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="bdf2d-113">目前版本的.NET framework 一律設定`dwAssemblyFlags`為此值。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="bdf2d-114">-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 」 值，指出組件是常駐承載。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="bdf2d-115">目前的.NET framework 版本永遠不會設定`dwAssemblyFlags`為此值。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="bdf2d-116">總大小，以 kb 為單位的組件包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="bdf2d-117">資訊清單檔案會保留目前的路徑字串緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="bdf2d-118">路徑必須以 null 字元結尾。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="bdf2d-119">的寬字元數目，包括 null 結束字元，`pszCurrentAssemblyPathBuf`包含。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdf2d-120">需求</span><span class="sxs-lookup"><span data-stu-id="bdf2d-120">Requirements</span></span>  
 <span data-ttu-id="bdf2d-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf2d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf2d-122">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bdf2d-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bdf2d-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf2d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf2d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdf2d-124">See also</span></span>

- [<span data-ttu-id="bdf2d-125">融合結構</span><span class="sxs-lookup"><span data-stu-id="bdf2d-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [<span data-ttu-id="bdf2d-126">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="bdf2d-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)

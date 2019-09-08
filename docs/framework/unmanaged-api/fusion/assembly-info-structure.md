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
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795481"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="a02ae-102">ASSEMBLY_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="a02ae-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="a02ae-103">包含在全域組件快取中註冊之元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a02ae-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="a02ae-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a02ae-105">成員</span><span class="sxs-lookup"><span data-stu-id="a02ae-105">Members</span></span>  
  
|<span data-ttu-id="a02ae-106">成員</span><span class="sxs-lookup"><span data-stu-id="a02ae-106">Member</span></span>|<span data-ttu-id="a02ae-107">描述</span><span class="sxs-lookup"><span data-stu-id="a02ae-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="a02ae-108">結構的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a02ae-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="a02ae-109">此欄位保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="a02ae-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="a02ae-110">旗標，指出元件的安裝詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a02ae-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="a02ae-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="a02ae-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="a02ae-112">-ASSEMBLYINFO_FLAG_INSTALLED 值，表示已安裝元件。</span><span class="sxs-lookup"><span data-stu-id="a02ae-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="a02ae-113">目前的 .NET Framework 版本一律會將設定`dwAssemblyFlags`為這個值。</span><span class="sxs-lookup"><span data-stu-id="a02ae-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="a02ae-114">-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 值，表示元件是裝載常駐的。</span><span class="sxs-lookup"><span data-stu-id="a02ae-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="a02ae-115">目前的 .NET Framework 版本永遠不會將`dwAssemblyFlags`設定為這個值。</span><span class="sxs-lookup"><span data-stu-id="a02ae-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="a02ae-116">元件所包含之檔案的總大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="a02ae-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="a02ae-117">字串緩衝區的指標，其中包含資訊清單檔案的目前路徑。</span><span class="sxs-lookup"><span data-stu-id="a02ae-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="a02ae-118">路徑的結尾必須是 null 字元。</span><span class="sxs-lookup"><span data-stu-id="a02ae-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="a02ae-119">`pszCurrentAssemblyPathBuf`包含的寬字元數目，包括 null 結束字元。</span><span class="sxs-lookup"><span data-stu-id="a02ae-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a02ae-120">需求</span><span class="sxs-lookup"><span data-stu-id="a02ae-120">Requirements</span></span>  
 <span data-ttu-id="a02ae-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a02ae-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02ae-122">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="a02ae-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a02ae-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02ae-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02ae-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a02ae-124">See also</span></span>

- [<span data-ttu-id="a02ae-125">融合結構</span><span class="sxs-lookup"><span data-stu-id="a02ae-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="a02ae-126">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="a02ae-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)

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
ms.openlocfilehash: 520a24ced6e897d926ce68ef5973ab7083731b9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717624"
---
# <a name="assembly_info-structure"></a><span data-ttu-id="7efa1-102">ASSEMBLY_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="7efa1-102">ASSEMBLY_INFO Structure</span></span>

<span data-ttu-id="7efa1-103">包含在全域組件快取中註冊之元件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7efa1-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7efa1-104">語法</span><span class="sxs-lookup"><span data-stu-id="7efa1-104">Syntax</span></span>  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="7efa1-105">成員</span><span class="sxs-lookup"><span data-stu-id="7efa1-105">Members</span></span>  
  
|<span data-ttu-id="7efa1-106">member</span><span class="sxs-lookup"><span data-stu-id="7efa1-106">Member</span></span>|<span data-ttu-id="7efa1-107">描述</span><span class="sxs-lookup"><span data-stu-id="7efa1-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="7efa1-108">結構的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7efa1-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="7efa1-109">這個欄位是保留給未來的擴充性。</span><span class="sxs-lookup"><span data-stu-id="7efa1-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="7efa1-110">旗標，指出元件的安裝詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7efa1-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="7efa1-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="7efa1-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="7efa1-112">-ASSEMBLYINFO_FLAG_INSTALLED 值，表示已安裝元件。</span><span class="sxs-lookup"><span data-stu-id="7efa1-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="7efa1-113">目前的 .NET Framework 版本一律會設定 `dwAssemblyFlags` 為此值。</span><span class="sxs-lookup"><span data-stu-id="7efa1-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="7efa1-114">-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 值，表示元件是裝載的裝載。</span><span class="sxs-lookup"><span data-stu-id="7efa1-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="7efa1-115">目前的 .NET Framework 版本永遠不會設定 `dwAssemblyFlags` 為此值。</span><span class="sxs-lookup"><span data-stu-id="7efa1-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="7efa1-116">元件所包含檔案的總大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="7efa1-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="7efa1-117">字串緩衝區的指標，此字串緩衝區會保存資訊清單檔案的目前路徑。</span><span class="sxs-lookup"><span data-stu-id="7efa1-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="7efa1-118">路徑的結尾必須是 null 字元。</span><span class="sxs-lookup"><span data-stu-id="7efa1-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="7efa1-119">包含的寬字元數（包括 null 結束字元） `pszCurrentAssemblyPathBuf` 。</span><span class="sxs-lookup"><span data-stu-id="7efa1-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7efa1-120">需求</span><span class="sxs-lookup"><span data-stu-id="7efa1-120">Requirements</span></span>  

 <span data-ttu-id="7efa1-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7efa1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7efa1-122">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="7efa1-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7efa1-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7efa1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efa1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7efa1-124">See also</span></span>

- [<span data-ttu-id="7efa1-125">融合結構</span><span class="sxs-lookup"><span data-stu-id="7efa1-125">Fusion Structures</span></span>](fusion-structures.md)
- [<span data-ttu-id="7efa1-126">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="7efa1-126">Global Assembly Cache</span></span>](../../app-domains/gac.md)

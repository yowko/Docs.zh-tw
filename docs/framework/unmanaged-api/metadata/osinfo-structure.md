---
title: OSINFO 結構
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a36cd3c5fb638799a735e4b4a1a98959500300b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761593"
---
# <a name="osinfo-structure"></a><span data-ttu-id="ee836-102">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="ee836-102">OSINFO Structure</span></span>
<span data-ttu-id="ee836-103">包含組件或模組的作業系統的相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ee836-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee836-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee836-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="ee836-105">成員</span><span class="sxs-lookup"><span data-stu-id="ee836-105">Members</span></span>  
  
|<span data-ttu-id="ee836-106">成員</span><span class="sxs-lookup"><span data-stu-id="ee836-106">Member</span></span>|<span data-ttu-id="ee836-107">說明</span><span class="sxs-lookup"><span data-stu-id="ee836-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="ee836-108">Microsoft Windows 平台函式所定義的識別碼值的其中一個`GetVersionEx`。</span><span class="sxs-lookup"><span data-stu-id="ee836-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="ee836-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="ee836-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="ee836-110">-VER_PLATFORM_WIN32s 或 0x0000，指定 Microsoft Windows 3.1。</span><span class="sxs-lookup"><span data-stu-id="ee836-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="ee836-111">-VER_PLATFORM_WIN32_WINDOWS 或 0x0001，指定 Windows 95、 Windows 98 或從它們繼承而來的作業系統。</span><span class="sxs-lookup"><span data-stu-id="ee836-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="ee836-112">-VER_PLATFORM_WIN32_NT 或 0x0010，指定 Windows NT 或從它繼承而來的作業系統。</span><span class="sxs-lookup"><span data-stu-id="ee836-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="ee836-113">作業系統主要版本或 NULL 值，指出任何版本。</span><span class="sxs-lookup"><span data-stu-id="ee836-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="ee836-114">作業系統次要版本或 NULL 值，指出任何版本。</span><span class="sxs-lookup"><span data-stu-id="ee836-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee836-115">備註</span><span class="sxs-lookup"><span data-stu-id="ee836-115">Remarks</span></span>  
 <span data-ttu-id="ee836-116">`OSINFO` 根據`OSVERSIONINFOEX`結構，也就是用於的 Microsoft Windows 平台函式呼叫`GetVersionEx`。</span><span class="sxs-lookup"><span data-stu-id="ee836-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="ee836-117">ASSEMBLYMETADATA 結構使用這個結構表示其作業系統支援。</span><span class="sxs-lookup"><span data-stu-id="ee836-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee836-118">需求</span><span class="sxs-lookup"><span data-stu-id="ee836-118">Requirements</span></span>  
 <span data-ttu-id="ee836-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee836-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee836-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee836-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee836-121">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ee836-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee836-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee836-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee836-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee836-123">See also</span></span>

- [<span data-ttu-id="ee836-124">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="ee836-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="ee836-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ee836-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

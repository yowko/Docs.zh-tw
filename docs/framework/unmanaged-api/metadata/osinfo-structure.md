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
ms.openlocfilehash: 49e29cc0367d5162dffcd641b163fd7b9a56ffd0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672873"
---
# <a name="osinfo-structure"></a><span data-ttu-id="12308-102">OSINFO 結構</span><span class="sxs-lookup"><span data-stu-id="12308-102">OSINFO Structure</span></span>

<span data-ttu-id="12308-103">包含元件或模組之作業系統的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="12308-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12308-104">語法</span><span class="sxs-lookup"><span data-stu-id="12308-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="12308-105">成員</span><span class="sxs-lookup"><span data-stu-id="12308-105">Members</span></span>  
  
|<span data-ttu-id="12308-106">member</span><span class="sxs-lookup"><span data-stu-id="12308-106">Member</span></span>|<span data-ttu-id="12308-107">描述</span><span class="sxs-lookup"><span data-stu-id="12308-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="12308-108">Microsoft Windows platform 函數所定義的其中一個識別碼值 `GetVersionEx` 。</span><span class="sxs-lookup"><span data-stu-id="12308-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="12308-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="12308-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="12308-110">-VER_PLATFORM_WIN32s （或0x0000），以指定 Microsoft Windows 3.1。</span><span class="sxs-lookup"><span data-stu-id="12308-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="12308-111">-VER_PLATFORM_WIN32_WINDOWS （或0x0001），指定 Windows 95、Windows 98 或其上的作業系統。</span><span class="sxs-lookup"><span data-stu-id="12308-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="12308-112">-VER_PLATFORM_WIN32_NT （或0x0002），以指定從其下衍生的 Windows NT 或作業系統。</span><span class="sxs-lookup"><span data-stu-id="12308-112">-   VER_PLATFORM_WIN32_NT, or 0x0002, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="12308-113">作業系統主要版本，或指出任何版本的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12308-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="12308-114">作業系統次要版本，或指出任何版本的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="12308-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12308-115">備註</span><span class="sxs-lookup"><span data-stu-id="12308-115">Remarks</span></span>  

 <span data-ttu-id="12308-116">`OSINFO` 以 `OSVERSIONINFOEX` 用來呼叫 Microsoft Windows platform function 的結構為基礎 `GetVersionEx` 。</span><span class="sxs-lookup"><span data-stu-id="12308-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="12308-117">ASSEMBLYMETADATA 結構會使用此結構來指出其作業系統支援。</span><span class="sxs-lookup"><span data-stu-id="12308-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12308-118">需求</span><span class="sxs-lookup"><span data-stu-id="12308-118">Requirements</span></span>  

 <span data-ttu-id="12308-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12308-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12308-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="12308-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12308-121">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="12308-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12308-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12308-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12308-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12308-123">See also</span></span>

- [<span data-ttu-id="12308-124">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="12308-124">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="12308-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="12308-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

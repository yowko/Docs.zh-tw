---
title: AssemblyFlags 列舉
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: ffb5953c843a338b4548253457a0c3b1ca0c20f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444308"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="cff5c-102">AssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="cff5c-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="cff5c-103">包含描述元件執行時間功能的值。</span><span class="sxs-lookup"><span data-stu-id="cff5c-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cff5c-104">語法</span><span class="sxs-lookup"><span data-stu-id="cff5c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cff5c-105">Members</span><span class="sxs-lookup"><span data-stu-id="cff5c-105">Members</span></span>  
  
|<span data-ttu-id="cff5c-106">成員</span><span class="sxs-lookup"><span data-stu-id="cff5c-106">Member</span></span>|<span data-ttu-id="cff5c-107">描述</span><span class="sxs-lookup"><span data-stu-id="cff5c-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="cff5c-108">指定匯出的類型定義在組成元件的檔案中是隱含的。</span><span class="sxs-lookup"><span data-stu-id="cff5c-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="cff5c-109">在 .NET Framework 版本1.0 和1.1 中，一律假設已設定此值。</span><span class="sxs-lookup"><span data-stu-id="cff5c-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="cff5c-110">指定資源定義在組成元件的檔案中是隱含的。</span><span class="sxs-lookup"><span data-stu-id="cff5c-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="cff5c-111">在 .NET Framework 1.0 和1.1 中，一律假設已設定此值。</span><span class="sxs-lookup"><span data-stu-id="cff5c-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="cff5c-112">指定如果元件在相同的應用程式域中執行，則無法與其他版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="cff5c-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="cff5c-113">指定如果元件在相同的進程中執行，則無法與其他版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="cff5c-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="cff5c-114">指定如果元件在同一部電腦上執行，則無法與其他版本一起執行。</span><span class="sxs-lookup"><span data-stu-id="cff5c-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cff5c-115">備註</span><span class="sxs-lookup"><span data-stu-id="cff5c-115">Remarks</span></span>  
 <span data-ttu-id="cff5c-116">0x0010 和0x0070 之間的值（含）是用來描述所參考元件的並存相容性功能。</span><span class="sxs-lookup"><span data-stu-id="cff5c-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="cff5c-117">如果未設定這些值，則會假設元件與並存相容。</span><span class="sxs-lookup"><span data-stu-id="cff5c-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cff5c-118">需求</span><span class="sxs-lookup"><span data-stu-id="cff5c-118">Requirements</span></span>  
 <span data-ttu-id="cff5c-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cff5c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff5c-120">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="cff5c-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="cff5c-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cff5c-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cff5c-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cff5c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff5c-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="cff5c-123">See also</span></span>

- [<span data-ttu-id="cff5c-124">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="cff5c-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="cff5c-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="cff5c-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

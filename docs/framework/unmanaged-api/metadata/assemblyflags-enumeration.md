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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c86a4fd2788c8ea2df5d9e54c5c221afd179704
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091417"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="fc9c8-102">AssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="fc9c8-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="fc9c8-103">包含描述的組件的執行階段功能的值。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc9c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc9c8-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fc9c8-105">成員</span><span class="sxs-lookup"><span data-stu-id="fc9c8-105">Members</span></span>  
  
|<span data-ttu-id="fc9c8-106">成員</span><span class="sxs-lookup"><span data-stu-id="fc9c8-106">Member</span></span>|<span data-ttu-id="fc9c8-107">描述</span><span class="sxs-lookup"><span data-stu-id="fc9c8-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="fc9c8-108">指定匯出的型別定義隱含構成組件檔案中。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="fc9c8-109">在.NET framework 1.0 和 1.1 版中，這個值永遠都會假設設定。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="fc9c8-110">指定的資源定義中是隱含包含組件的檔案。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="fc9c8-111">在.NET Framework 1.0 和 1.1 中，這個值永遠都會假設設定。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="fc9c8-112">指定是否它們相同的應用程式定義域中執行，無法與其他版本一起執行的組件。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="fc9c8-113">指定是否它們在相同的程序執行，無法與其他版本一起執行的組件。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="fc9c8-114">指定是否在同一部電腦上執行，無法與其他版本一起執行的組件。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc9c8-115">備註</span><span class="sxs-lookup"><span data-stu-id="fc9c8-115">Remarks</span></span>  
 <span data-ttu-id="fc9c8-116">0x0010 與 0x0070 之間的值用來描述所參考組件的並排顯示相容性功能。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="fc9c8-117">如果沒有這些值的設定，則會將組件假設為並排顯示相容。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc9c8-118">需求</span><span class="sxs-lookup"><span data-stu-id="fc9c8-118">Requirements</span></span>  
 <span data-ttu-id="fc9c8-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc9c8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc9c8-120">**標頭：** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc9c8-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="fc9c8-121">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fc9c8-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="fc9c8-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="fc9c8-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc9c8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc9c8-123">See also</span></span>

- [<span data-ttu-id="fc9c8-124">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="fc9c8-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="fc9c8-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fc9c8-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

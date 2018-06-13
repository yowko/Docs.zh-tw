---
title: CorPEKind 列舉
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5869eb16bd768d58a6f27a83f2d8d51914a8aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443111"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="2e599-102">CorPEKind 列舉</span><span class="sxs-lookup"><span data-stu-id="2e599-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="2e599-103">包含描述可攜式執行檔 (PE)，值傳回呼叫[imetadataimport2:: Getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)。</span><span class="sxs-lookup"><span data-stu-id="2e599-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e599-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e599-104">Syntax</span></span>  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="2e599-105">成員</span><span class="sxs-lookup"><span data-stu-id="2e599-105">Members</span></span>  
  
|<span data-ttu-id="2e599-106">成員</span><span class="sxs-lookup"><span data-stu-id="2e599-106">Member</span></span>|<span data-ttu-id="2e599-107">描述</span><span class="sxs-lookup"><span data-stu-id="2e599-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="2e599-108">指出這不是 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="2e599-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="2e599-109">表示此 PE 檔包含只受管理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2e599-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="2e599-110">指出此 PE 檔案，會呼叫 Win32。</span><span class="sxs-lookup"><span data-stu-id="2e599-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="2e599-111">表示在 64 位元平台上執行此 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="2e599-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="2e599-112">表示此 PE 檔是原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="2e599-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="2e599-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="2e599-113">pe32BitPreferred</span></span>|<span data-ttu-id="2e599-114">指出此 PE 檔案是平台限制，而且偏好在 32 位元環境中載入。</span><span class="sxs-lookup"><span data-stu-id="2e599-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e599-115">備註</span><span class="sxs-lookup"><span data-stu-id="2e599-115">Remarks</span></span>  
 <span data-ttu-id="2e599-116">以位元的組合，可以使用這些值。</span><span class="sxs-lookup"><span data-stu-id="2e599-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e599-117">需求</span><span class="sxs-lookup"><span data-stu-id="2e599-117">Requirements</span></span>  
 <span data-ttu-id="2e599-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e599-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e599-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2e599-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2e599-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e599-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e599-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e599-121">See Also</span></span>  
 [<span data-ttu-id="2e599-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="2e599-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

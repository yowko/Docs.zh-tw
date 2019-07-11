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
ms.openlocfilehash: 0bfe30567bcd8e22a82d401e00b0a6ee50407def
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781676"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="8c83e-102">CorPEKind 列舉</span><span class="sxs-lookup"><span data-stu-id="8c83e-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="8c83e-103">包含值，描述可移植執行檔 (PE) 檔案，從呼叫傳回[IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)。</span><span class="sxs-lookup"><span data-stu-id="8c83e-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c83e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c83e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="8c83e-105">成員</span><span class="sxs-lookup"><span data-stu-id="8c83e-105">Members</span></span>  
  
|<span data-ttu-id="8c83e-106">成員</span><span class="sxs-lookup"><span data-stu-id="8c83e-106">Member</span></span>|<span data-ttu-id="8c83e-107">描述</span><span class="sxs-lookup"><span data-stu-id="8c83e-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="8c83e-108">指出這不是 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="8c83e-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="8c83e-109">表示此 PE 檔包含只受管理的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8c83e-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="8c83e-110">指出此 PE 檔會 Win32 呼叫。</span><span class="sxs-lookup"><span data-stu-id="8c83e-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="8c83e-111">表示在 64 位元平台上執行此 PE 檔。</span><span class="sxs-lookup"><span data-stu-id="8c83e-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="8c83e-112">指出此 PE 檔案是原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="8c83e-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="8c83e-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="8c83e-113">pe32BitPreferred</span></span>|<span data-ttu-id="8c83e-114">指出此 PE 檔是平台相關，而且偏好在 32 位元環境中載入。</span><span class="sxs-lookup"><span data-stu-id="8c83e-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c83e-115">備註</span><span class="sxs-lookup"><span data-stu-id="8c83e-115">Remarks</span></span>  
 <span data-ttu-id="8c83e-116">這些值可用以位元的組合。</span><span class="sxs-lookup"><span data-stu-id="8c83e-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c83e-117">需求</span><span class="sxs-lookup"><span data-stu-id="8c83e-117">Requirements</span></span>  
 <span data-ttu-id="8c83e-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c83e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c83e-119">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8c83e-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8c83e-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c83e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c83e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c83e-121">See also</span></span>

- [<span data-ttu-id="8c83e-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="8c83e-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

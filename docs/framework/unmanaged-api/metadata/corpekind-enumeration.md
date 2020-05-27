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
ms.openlocfilehash: 8b6eab8156f72847eb6dd3369950f9b46a3fc877
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007555"
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="d27e0-102">CorPEKind 列舉</span><span class="sxs-lookup"><span data-stu-id="d27e0-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="d27e0-103">包含值，描述從[IMetaDataImport2：： GetPEKind](imetadataimport2-getpekind-method.md)的呼叫傳回的可移植執行檔（PE）。</span><span class="sxs-lookup"><span data-stu-id="d27e0-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d27e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d27e0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d27e0-105">成員</span><span class="sxs-lookup"><span data-stu-id="d27e0-105">Members</span></span>  
  
|<span data-ttu-id="d27e0-106">成員</span><span class="sxs-lookup"><span data-stu-id="d27e0-106">Member</span></span>|<span data-ttu-id="d27e0-107">描述</span><span class="sxs-lookup"><span data-stu-id="d27e0-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="d27e0-108">表示這不是 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="d27e0-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="d27e0-109">指出這個 PE 檔案僅包含 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d27e0-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="d27e0-110">指出這個 PE 檔案會進行 Win32 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d27e0-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="d27e0-111">指出這個 PE 檔案是在64位平臺上執行。</span><span class="sxs-lookup"><span data-stu-id="d27e0-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="d27e0-112">指出這個 PE 檔案是機器碼。</span><span class="sxs-lookup"><span data-stu-id="d27e0-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="d27e0-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="d27e0-113">pe32BitPreferred</span></span>|<span data-ttu-id="d27e0-114">指出此 PE 檔案為平臺中性，並偏好在32位環境中載入。</span><span class="sxs-lookup"><span data-stu-id="d27e0-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d27e0-115">備註</span><span class="sxs-lookup"><span data-stu-id="d27e0-115">Remarks</span></span>  
 <span data-ttu-id="d27e0-116">這些值可用於位組合。</span><span class="sxs-lookup"><span data-stu-id="d27e0-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d27e0-117">需求</span><span class="sxs-lookup"><span data-stu-id="d27e0-117">Requirements</span></span>  
 <span data-ttu-id="d27e0-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d27e0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d27e0-119">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="d27e0-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d27e0-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d27e0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27e0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d27e0-121">See also</span></span>

- [<span data-ttu-id="d27e0-122">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="d27e0-122">Metadata Enumerations</span></span>](metadata-enumerations.md)

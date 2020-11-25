---
title: CorFileMapping 列舉
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 63e27a62e176a92b03c10b59a55d9da3192918f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726111"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="a36b2-102">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="a36b2-102">CorFileMapping Enumeration</span></span>

<span data-ttu-id="a36b2-103">包含值，這些值會描述從 [IMetaDataInfo：： GetFileMapping](imetadatainfo-getfilemapping-method.md) 方法的呼叫所傳回的檔案對應類型。</span><span class="sxs-lookup"><span data-stu-id="a36b2-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a36b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a36b2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="a36b2-105">成員</span><span class="sxs-lookup"><span data-stu-id="a36b2-105">Members</span></span>  
  
|<span data-ttu-id="a36b2-106">member</span><span class="sxs-lookup"><span data-stu-id="a36b2-106">Member</span></span>|<span data-ttu-id="a36b2-107">描述</span><span class="sxs-lookup"><span data-stu-id="a36b2-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="a36b2-108">檔案會對應為資料檔案。</span><span class="sxs-lookup"><span data-stu-id="a36b2-108">The file is mapped as a data file.</span></span> <span data-ttu-id="a36b2-109">也就是說，旗標 `SEC_IMAGE` 未傳遞至 Microsoft Win32 `CreateFileMapping` 函數。</span><span class="sxs-lookup"><span data-stu-id="a36b2-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="a36b2-110">使用函式 `LoadLibrary` 或具有旗標的函式，以對應檔案來執行 `CreateFileMapping` `SEC_IMAGE` 。</span><span class="sxs-lookup"><span data-stu-id="a36b2-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a36b2-111">需求</span><span class="sxs-lookup"><span data-stu-id="a36b2-111">Requirements</span></span>  

 <span data-ttu-id="a36b2-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a36b2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a36b2-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="a36b2-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a36b2-114">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a36b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36b2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a36b2-115">See also</span></span>

- [<span data-ttu-id="a36b2-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="a36b2-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="a36b2-117">GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="a36b2-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)

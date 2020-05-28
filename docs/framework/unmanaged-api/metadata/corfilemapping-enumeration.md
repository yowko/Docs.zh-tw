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
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007386"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="b47f0-102">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="b47f0-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="b47f0-103">包含值，描述從[IMetaDataInfo：： GetFileMapping](imetadatainfo-getfilemapping-method.md)方法的呼叫所傳回的檔對應類型。</span><span class="sxs-lookup"><span data-stu-id="b47f0-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b47f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="b47f0-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="b47f0-105">成員</span><span class="sxs-lookup"><span data-stu-id="b47f0-105">Members</span></span>  
  
|<span data-ttu-id="b47f0-106">成員</span><span class="sxs-lookup"><span data-stu-id="b47f0-106">Member</span></span>|<span data-ttu-id="b47f0-107">描述</span><span class="sxs-lookup"><span data-stu-id="b47f0-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="b47f0-108">檔案會對應為資料檔案。</span><span class="sxs-lookup"><span data-stu-id="b47f0-108">The file is mapped as a data file.</span></span> <span data-ttu-id="b47f0-109">也就是說，旗標 `SEC_IMAGE` 不會傳遞至 Microsoft Win32 `CreateFileMapping` 函數。</span><span class="sxs-lookup"><span data-stu-id="b47f0-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="b47f0-110">檔案會對應執行，方法是使用函式 `LoadLibrary` 或 `CreateFileMapping` 函數搭配旗標 `SEC_IMAGE` 。</span><span class="sxs-lookup"><span data-stu-id="b47f0-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b47f0-111">需求</span><span class="sxs-lookup"><span data-stu-id="b47f0-111">Requirements</span></span>  
 <span data-ttu-id="b47f0-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b47f0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b47f0-113">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="b47f0-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b47f0-114">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b47f0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47f0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b47f0-115">See also</span></span>

- [<span data-ttu-id="b47f0-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="b47f0-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="b47f0-117">GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="b47f0-117">GetFileMapping Method</span></span>](imetadatainfo-getfilemapping-method.md)

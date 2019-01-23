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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9b3802c9c72ec3a9302e403e55789aab8102cf1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624986"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="af0ff-102">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="af0ff-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="af0ff-103">包含描述類型的檔案對應呼叫所傳回的值[imetadatainfo:: Getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="af0ff-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af0ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="af0ff-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="af0ff-105">成員</span><span class="sxs-lookup"><span data-stu-id="af0ff-105">Members</span></span>  
  
|<span data-ttu-id="af0ff-106">成員</span><span class="sxs-lookup"><span data-stu-id="af0ff-106">Member</span></span>|<span data-ttu-id="af0ff-107">描述</span><span class="sxs-lookup"><span data-stu-id="af0ff-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="af0ff-108">檔案會當做資料檔對應。</span><span class="sxs-lookup"><span data-stu-id="af0ff-108">The file is mapped as a data file.</span></span> <span data-ttu-id="af0ff-109">亦即`SEC_IMAGE`旗標不傳遞至 Microsoft Win32`CreateFileMapping`函式。</span><span class="sxs-lookup"><span data-stu-id="af0ff-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="af0ff-110">檔案對應來執行，使用其中一種`LoadLibrary`函式或`CreateFileMapping`函式搭配`SEC_IMAGE`旗標。</span><span class="sxs-lookup"><span data-stu-id="af0ff-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af0ff-111">需求</span><span class="sxs-lookup"><span data-stu-id="af0ff-111">Requirements</span></span>  
 <span data-ttu-id="af0ff-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af0ff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af0ff-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="af0ff-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="af0ff-114">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af0ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0ff-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af0ff-115">See also</span></span>
- [<span data-ttu-id="af0ff-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="af0ff-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="af0ff-117">GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="af0ff-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)

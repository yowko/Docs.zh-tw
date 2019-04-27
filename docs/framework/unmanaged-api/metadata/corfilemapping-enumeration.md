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
ms.openlocfilehash: a3056836d289383161f9fa538c3c6349f88b6ba6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905732"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="e95a5-102">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="e95a5-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="e95a5-103">包含描述類型的檔案對應呼叫所傳回的值[imetadatainfo:: Getfilemapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e95a5-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e95a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="e95a5-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="e95a5-105">成員</span><span class="sxs-lookup"><span data-stu-id="e95a5-105">Members</span></span>  
  
|<span data-ttu-id="e95a5-106">成員</span><span class="sxs-lookup"><span data-stu-id="e95a5-106">Member</span></span>|<span data-ttu-id="e95a5-107">描述</span><span class="sxs-lookup"><span data-stu-id="e95a5-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="e95a5-108">檔案會當做資料檔對應。</span><span class="sxs-lookup"><span data-stu-id="e95a5-108">The file is mapped as a data file.</span></span> <span data-ttu-id="e95a5-109">亦即`SEC_IMAGE`旗標不傳遞至 Microsoft Win32`CreateFileMapping`函式。</span><span class="sxs-lookup"><span data-stu-id="e95a5-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="e95a5-110">檔案對應來執行，使用其中一種`LoadLibrary`函式或`CreateFileMapping`函式搭配`SEC_IMAGE`旗標。</span><span class="sxs-lookup"><span data-stu-id="e95a5-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e95a5-111">需求</span><span class="sxs-lookup"><span data-stu-id="e95a5-111">Requirements</span></span>  
 <span data-ttu-id="e95a5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e95a5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e95a5-113">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e95a5-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e95a5-114">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e95a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95a5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e95a5-115">See also</span></span>

- [<span data-ttu-id="e95a5-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="e95a5-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="e95a5-117">GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="e95a5-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)

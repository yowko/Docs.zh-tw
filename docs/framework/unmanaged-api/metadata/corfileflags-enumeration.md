---
title: CorFileFlags 列舉
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
ms.openlocfilehash: c315e2ae2753b59b4e277764d27c3fb3388b515c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445426"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="f7f2c-102">CorFileFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="f7f2c-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="f7f2c-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="f7f2c-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7f2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7f2c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f7f2c-105">Members</span><span class="sxs-lookup"><span data-stu-id="f7f2c-105">Members</span></span>  
  
|<span data-ttu-id="f7f2c-106">成員</span><span class="sxs-lookup"><span data-stu-id="f7f2c-106">Member</span></span>|<span data-ttu-id="f7f2c-107">描述</span><span class="sxs-lookup"><span data-stu-id="f7f2c-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="f7f2c-108">Indicates that the file is not a resource file.</span><span class="sxs-lookup"><span data-stu-id="f7f2c-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="f7f2c-109">Indicates that the file, possibly a resource file, does not contain metadata.</span><span class="sxs-lookup"><span data-stu-id="f7f2c-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7f2c-110">需求</span><span class="sxs-lookup"><span data-stu-id="f7f2c-110">Requirements</span></span>  
 <span data-ttu-id="f7f2c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7f2c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7f2c-112">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f7f2c-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f7f2c-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7f2c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f2c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7f2c-114">See also</span></span>

- [<span data-ttu-id="f7f2c-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f7f2c-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

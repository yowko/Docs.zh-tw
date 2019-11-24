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
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450289"
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="7c98d-102">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="7c98d-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="7c98d-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="7c98d-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c98d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c98d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="7c98d-105">Members</span><span class="sxs-lookup"><span data-stu-id="7c98d-105">Members</span></span>  
  
|<span data-ttu-id="7c98d-106">成員</span><span class="sxs-lookup"><span data-stu-id="7c98d-106">Member</span></span>|<span data-ttu-id="7c98d-107">描述</span><span class="sxs-lookup"><span data-stu-id="7c98d-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="7c98d-108">The file is mapped as a data file.</span><span class="sxs-lookup"><span data-stu-id="7c98d-108">The file is mapped as a data file.</span></span> <span data-ttu-id="7c98d-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span><span class="sxs-lookup"><span data-stu-id="7c98d-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="7c98d-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span><span class="sxs-lookup"><span data-stu-id="7c98d-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c98d-111">需求</span><span class="sxs-lookup"><span data-stu-id="7c98d-111">Requirements</span></span>  
 <span data-ttu-id="7c98d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c98d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c98d-113">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7c98d-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7c98d-114">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c98d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c98d-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c98d-115">See also</span></span>

- [<span data-ttu-id="7c98d-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="7c98d-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="7c98d-117">GetFileMapping 方法</span><span class="sxs-lookup"><span data-stu-id="7c98d-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)

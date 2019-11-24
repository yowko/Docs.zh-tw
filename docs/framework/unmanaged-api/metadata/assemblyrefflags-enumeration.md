---
title: AssemblyRefFlags 列舉
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 23d293a87112c62cb2127b435faeca258a7de226
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444218"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="2837b-102">AssemblyRefFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="2837b-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="2837b-103">Contains values that describe features of an assembly reference.</span><span class="sxs-lookup"><span data-stu-id="2837b-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2837b-104">語法</span><span class="sxs-lookup"><span data-stu-id="2837b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2837b-105">Members</span><span class="sxs-lookup"><span data-stu-id="2837b-105">Members</span></span>  
  
|<span data-ttu-id="2837b-106">成員</span><span class="sxs-lookup"><span data-stu-id="2837b-106">Member</span></span>|<span data-ttu-id="2837b-107">描述</span><span class="sxs-lookup"><span data-stu-id="2837b-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="2837b-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span><span class="sxs-lookup"><span data-stu-id="2837b-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2837b-109">需求</span><span class="sxs-lookup"><span data-stu-id="2837b-109">Requirements</span></span>  
 <span data-ttu-id="2837b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2837b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2837b-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2837b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2837b-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2837b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2837b-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="2837b-113">See also</span></span>

- [<span data-ttu-id="2837b-114">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="2837b-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="2837b-115">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2837b-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="2837b-116">DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="2837b-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)

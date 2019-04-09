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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc98b2421d23ffd6dfb716a8cc782b46a9d59ce0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128891"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="c8d31-102">AssemblyRefFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="c8d31-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="c8d31-103">包含值，描述組件參考的功能。</span><span class="sxs-lookup"><span data-stu-id="c8d31-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8d31-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8d31-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c8d31-105">成員</span><span class="sxs-lookup"><span data-stu-id="c8d31-105">Members</span></span>  
  
|<span data-ttu-id="c8d31-106">成員</span><span class="sxs-lookup"><span data-stu-id="c8d31-106">Member</span></span>|<span data-ttu-id="c8d31-107">描述</span><span class="sxs-lookup"><span data-stu-id="c8d31-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="c8d31-108">指定組件參考，包含完整的雜湊發行者的相關資訊的組件。</span><span class="sxs-lookup"><span data-stu-id="c8d31-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8d31-109">需求</span><span class="sxs-lookup"><span data-stu-id="c8d31-109">Requirements</span></span>  
 <span data-ttu-id="c8d31-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8d31-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8d31-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c8d31-111">**Header:** Cor.h</span></span>  
  
 **<span data-ttu-id="c8d31-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c8d31-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8d31-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8d31-113">See also</span></span>

- [<span data-ttu-id="c8d31-114">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="c8d31-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="c8d31-115">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c8d31-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="c8d31-116">DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="c8d31-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)

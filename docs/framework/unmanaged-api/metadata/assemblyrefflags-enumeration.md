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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043312"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="0e762-102">AssemblyRefFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="0e762-102">AssemblyRefFlags Enumeration</span></span>
<span data-ttu-id="0e762-103">包含值，描述組件參考的功能。</span><span class="sxs-lookup"><span data-stu-id="0e762-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e762-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e762-104">Syntax</span></span>  
  
```  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="0e762-105">成員</span><span class="sxs-lookup"><span data-stu-id="0e762-105">Members</span></span>  
  
|<span data-ttu-id="0e762-106">成員</span><span class="sxs-lookup"><span data-stu-id="0e762-106">Member</span></span>|<span data-ttu-id="0e762-107">描述</span><span class="sxs-lookup"><span data-stu-id="0e762-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="0e762-108">指定組件參考，包含完整的雜湊發行者的相關資訊的組件。</span><span class="sxs-lookup"><span data-stu-id="0e762-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e762-109">需求</span><span class="sxs-lookup"><span data-stu-id="0e762-109">Requirements</span></span>  
 <span data-ttu-id="0e762-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e762-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e762-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e762-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e762-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e762-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e762-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e762-113">See also</span></span>

- [<span data-ttu-id="0e762-114">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="0e762-114">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="0e762-115">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="0e762-115">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="0e762-116">DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="0e762-116">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)

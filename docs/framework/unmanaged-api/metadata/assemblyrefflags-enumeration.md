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
ms.openlocfilehash: 0a99d2f79645bdc46ff4db86d7280614eeb1faf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732758"
---
# <a name="assemblyrefflags-enumeration"></a><span data-ttu-id="61ab9-102">AssemblyRefFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="61ab9-102">AssemblyRefFlags Enumeration</span></span>

<span data-ttu-id="61ab9-103">包含描述元件參考功能的值。</span><span class="sxs-lookup"><span data-stu-id="61ab9-103">Contains values that describe features of an assembly reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ab9-104">語法</span><span class="sxs-lookup"><span data-stu-id="61ab9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="61ab9-105">成員</span><span class="sxs-lookup"><span data-stu-id="61ab9-105">Members</span></span>  
  
|<span data-ttu-id="61ab9-106">member</span><span class="sxs-lookup"><span data-stu-id="61ab9-106">Member</span></span>|<span data-ttu-id="61ab9-107">描述</span><span class="sxs-lookup"><span data-stu-id="61ab9-107">Description</span></span>|  
|------------|-----------------|  
|`arfFullOriginator`|<span data-ttu-id="61ab9-108">指定元件參考包含有關元件發行者的完整、未雜湊資訊。</span><span class="sxs-lookup"><span data-stu-id="61ab9-108">Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61ab9-109">需求</span><span class="sxs-lookup"><span data-stu-id="61ab9-109">Requirements</span></span>  

 <span data-ttu-id="61ab9-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61ab9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ab9-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="61ab9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61ab9-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ab9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ab9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61ab9-113">See also</span></span>

- [<span data-ttu-id="61ab9-114">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="61ab9-114">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="61ab9-115">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="61ab9-115">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="61ab9-116">DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="61ab9-116">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)

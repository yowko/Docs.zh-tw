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
ms.openlocfilehash: 70d789f417700734b546cac6ff527ed5aa84fcf9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688623"
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="00912-102">CorFileFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="00912-102">CorFileFlags Enumeration</span></span>

<span data-ttu-id="00912-103">包含值，這些值會描述在呼叫 [IMetaDataAssemblyEmit：:D efinefile](imetadataassemblyemit-definefile-method.md)中定義的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="00912-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00912-104">語法</span><span class="sxs-lookup"><span data-stu-id="00912-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="00912-105">成員</span><span class="sxs-lookup"><span data-stu-id="00912-105">Members</span></span>  
  
|<span data-ttu-id="00912-106">member</span><span class="sxs-lookup"><span data-stu-id="00912-106">Member</span></span>|<span data-ttu-id="00912-107">描述</span><span class="sxs-lookup"><span data-stu-id="00912-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="00912-108">指出檔案不是資源檔。</span><span class="sxs-lookup"><span data-stu-id="00912-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="00912-109">指出檔案（可能為資源檔）不包含中繼資料。</span><span class="sxs-lookup"><span data-stu-id="00912-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00912-110">需求</span><span class="sxs-lookup"><span data-stu-id="00912-110">Requirements</span></span>  

 <span data-ttu-id="00912-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00912-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00912-112">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="00912-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="00912-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00912-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00912-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00912-114">See also</span></span>

- [<span data-ttu-id="00912-115">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="00912-115">Metadata Enumerations</span></span>](metadata-enumerations.md)

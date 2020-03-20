---
title: CorPropertyAttr 列舉
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: 95a798d662b44cf2e088af84d3b1eec97da8e7fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177949"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="167ea-102">CorPropertyAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="167ea-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="167ea-103">包含值，這些值描述屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="167ea-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="167ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="167ea-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="167ea-105">成員</span><span class="sxs-lookup"><span data-stu-id="167ea-105">Members</span></span>  
  
|<span data-ttu-id="167ea-106">member</span><span class="sxs-lookup"><span data-stu-id="167ea-106">Member</span></span>|<span data-ttu-id="167ea-107">描述</span><span class="sxs-lookup"><span data-stu-id="167ea-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="167ea-108">指定屬性是特殊的，並且其名稱描述如何。</span><span class="sxs-lookup"><span data-stu-id="167ea-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="167ea-109">保留供公共語言運行時的內部使用。</span><span class="sxs-lookup"><span data-stu-id="167ea-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="167ea-110">指定通用語言運行時中繼資料內部 API 應檢查屬性名稱的編碼。</span><span class="sxs-lookup"><span data-stu-id="167ea-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="167ea-111">指定屬性具有預設值。</span><span class="sxs-lookup"><span data-stu-id="167ea-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="167ea-112">未使用的。</span><span class="sxs-lookup"><span data-stu-id="167ea-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="167ea-113">需求</span><span class="sxs-lookup"><span data-stu-id="167ea-113">Requirements</span></span>  
 <span data-ttu-id="167ea-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="167ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="167ea-115">**標題：** 科爾赫德</span><span class="sxs-lookup"><span data-stu-id="167ea-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="167ea-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="167ea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167ea-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="167ea-117">See also</span></span>

- [<span data-ttu-id="167ea-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="167ea-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

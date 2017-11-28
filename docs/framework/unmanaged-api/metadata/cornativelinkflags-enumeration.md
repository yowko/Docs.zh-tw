---
title: "CorNativeLinkFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkFlags
helpviewer_keywords: CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09afda63959d974af71e0264ad116c20d3af1923
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="d205b-102">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="d205b-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="d205b-103">提供連結器在連結機器碼時所使用的旗標值。</span><span class="sxs-lookup"><span data-stu-id="d205b-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d205b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d205b-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d205b-105">成員</span><span class="sxs-lookup"><span data-stu-id="d205b-105">Members</span></span>  
  
|<span data-ttu-id="d205b-106">成員</span><span class="sxs-lookup"><span data-stu-id="d205b-106">Member</span></span>|<span data-ttu-id="d205b-107">說明</span><span class="sxs-lookup"><span data-stu-id="d205b-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="d205b-108">表示沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="d205b-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="d205b-109">指出`setLastError`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d205b-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="d205b-110">指出`nomangle`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d205b-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="d205b-111">未使用。</span><span class="sxs-lookup"><span data-stu-id="d205b-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d205b-112">需求</span><span class="sxs-lookup"><span data-stu-id="d205b-112">Requirements</span></span>  
 <span data-ttu-id="d205b-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d205b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d205b-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d205b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d205b-115">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d205b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d205b-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d205b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d205b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d205b-117">See Also</span></span>  
 [<span data-ttu-id="d205b-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="d205b-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

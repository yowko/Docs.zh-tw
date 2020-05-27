---
title: COUNINITIEE 列舉
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
ms.openlocfilehash: 14942680a79c4d1fcc69092a4f752738db1fb0b0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008909"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="41dba-102">COUNINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="41dba-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="41dba-103">指定初始化 common language runtime 時， [CoUninitializeEE](../hosting/couninitializeee-function.md)所使用的常數。</span><span class="sxs-lookup"><span data-stu-id="41dba-103">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41dba-104">語法</span><span class="sxs-lookup"><span data-stu-id="41dba-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="41dba-105">成員</span><span class="sxs-lookup"><span data-stu-id="41dba-105">Members</span></span>  
  
|<span data-ttu-id="41dba-106">成員</span><span class="sxs-lookup"><span data-stu-id="41dba-106">Member</span></span>|<span data-ttu-id="41dba-107">描述</span><span class="sxs-lookup"><span data-stu-id="41dba-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="41dba-108">表示預設解除初始化模式。</span><span class="sxs-lookup"><span data-stu-id="41dba-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="41dba-109">表示卸載元件的解除初始化模式。</span><span class="sxs-lookup"><span data-stu-id="41dba-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41dba-110">需求</span><span class="sxs-lookup"><span data-stu-id="41dba-110">Requirements</span></span>  
 <span data-ttu-id="41dba-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41dba-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41dba-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="41dba-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41dba-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="41dba-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41dba-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41dba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dba-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41dba-115">See also</span></span>

- [<span data-ttu-id="41dba-116">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="41dba-116">Metadata Enumerations</span></span>](metadata-enumerations.md)

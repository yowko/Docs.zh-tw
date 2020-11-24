---
title: CorNativeLinkFlags 列舉
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: ef9b177bee0651b6b8ea994610315ce93524e8e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676929"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="ed71c-102">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="ed71c-102">CorNativeLinkFlags Enumeration</span></span>

<span data-ttu-id="ed71c-103">提供連結器在連結機器碼時所使用的旗標值。</span><span class="sxs-lookup"><span data-stu-id="ed71c-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed71c-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed71c-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ed71c-105">成員</span><span class="sxs-lookup"><span data-stu-id="ed71c-105">Members</span></span>  
  
|<span data-ttu-id="ed71c-106">member</span><span class="sxs-lookup"><span data-stu-id="ed71c-106">Member</span></span>|<span data-ttu-id="ed71c-107">描述</span><span class="sxs-lookup"><span data-stu-id="ed71c-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="ed71c-108">指出沒有旗標。</span><span class="sxs-lookup"><span data-stu-id="ed71c-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="ed71c-109">表示 `setLastError` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ed71c-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="ed71c-110">表示 `nomangle` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ed71c-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="ed71c-111">未使用。</span><span class="sxs-lookup"><span data-stu-id="ed71c-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed71c-112">需求</span><span class="sxs-lookup"><span data-stu-id="ed71c-112">Requirements</span></span>  

 <span data-ttu-id="ed71c-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed71c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed71c-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ed71c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed71c-115">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ed71c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed71c-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed71c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed71c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed71c-117">See also</span></span>

- [<span data-ttu-id="ed71c-118">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="ed71c-118">Metadata Enumerations</span></span>](metadata-enumerations.md)

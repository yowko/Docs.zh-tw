---
title: CorRegFlags 列舉
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: 5ea588194720394ad9f361fbba702f3fcdcbe110
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706095"
---
# <a name="corregflags-enumeration"></a><span data-ttu-id="13038-102">CorRegFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="13038-102">CorRegFlags Enumeration</span></span>

<span data-ttu-id="13038-103">提供在安裝模組或複合影像時用於註冊的旗標值。</span><span class="sxs-lookup"><span data-stu-id="13038-103">Provides flag values used for registration when installing a module or composite image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13038-104">語法</span><span class="sxs-lookup"><span data-stu-id="13038-104">Syntax</span></span>  
  
```cpp  
typedef enum
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="13038-105">成員</span><span class="sxs-lookup"><span data-stu-id="13038-105">Members</span></span>  
  
|<span data-ttu-id="13038-106">member</span><span class="sxs-lookup"><span data-stu-id="13038-106">Member</span></span>|<span data-ttu-id="13038-107">描述</span><span class="sxs-lookup"><span data-stu-id="13038-107">Description</span></span>|  
|------------|-----------------|  
|`regNoCopy`|<span data-ttu-id="13038-108">指定不應將檔案複製到目的地。</span><span class="sxs-lookup"><span data-stu-id="13038-108">Specifies that files should not be copied into the destination.</span></span>|  
|`regConfig`|<span data-ttu-id="13038-109">指定模組或複合為設定。</span><span class="sxs-lookup"><span data-stu-id="13038-109">Specifies that the module or composite is a configuration.</span></span>|  
|`regHasRefs`|<span data-ttu-id="13038-110">指定模組或複合具有類別參考。</span><span class="sxs-lookup"><span data-stu-id="13038-110">Specifies that the module or composite has class references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13038-111">需求</span><span class="sxs-lookup"><span data-stu-id="13038-111">Requirements</span></span>  

 <span data-ttu-id="13038-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13038-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13038-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="13038-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13038-114">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="13038-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13038-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13038-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13038-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13038-116">See also</span></span>

- [<span data-ttu-id="13038-117">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="13038-117">Metadata Enumerations</span></span>](metadata-enumerations.md)

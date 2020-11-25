---
title: CorRefToDefCheck 列舉
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e7ce604acddb88d5a15844cbce2622b21e364cc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706108"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="3ae00-102">CorRefToDefCheck 列舉</span><span class="sxs-lookup"><span data-stu-id="3ae00-102">CorRefToDefCheck Enumeration</span></span>

<span data-ttu-id="3ae00-103">指定旗標，以控制哪些參考的項目已轉換成其定義，以便最佳化程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ae00-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae00-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ae00-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="3ae00-105">成員</span><span class="sxs-lookup"><span data-stu-id="3ae00-105">Members</span></span>  
  
|<span data-ttu-id="3ae00-106">member</span><span class="sxs-lookup"><span data-stu-id="3ae00-106">Member</span></span>|<span data-ttu-id="3ae00-107">描述</span><span class="sxs-lookup"><span data-stu-id="3ae00-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="3ae00-108">指定應將型別參考和成員參考轉換成定義。</span><span class="sxs-lookup"><span data-stu-id="3ae00-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="3ae00-109">這是 (&#124;) 的預設值 `MDTypeRefToDef` `MDMemberRefToDef` 。</span><span class="sxs-lookup"><span data-stu-id="3ae00-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="3ae00-110">指定所有參考的專案都應轉換成定義。</span><span class="sxs-lookup"><span data-stu-id="3ae00-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="3ae00-111">指定不應將參考的專案轉換成定義。</span><span class="sxs-lookup"><span data-stu-id="3ae00-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="3ae00-112">指定只能將型別參考轉換成型別定義。</span><span class="sxs-lookup"><span data-stu-id="3ae00-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="3ae00-113">指定只有成員參考應轉換成定義。</span><span class="sxs-lookup"><span data-stu-id="3ae00-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="3ae00-114">也就是說，成員參考應轉換成方法定義或欄位定義。</span><span class="sxs-lookup"><span data-stu-id="3ae00-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ae00-115">需求</span><span class="sxs-lookup"><span data-stu-id="3ae00-115">Requirements</span></span>  

 <span data-ttu-id="3ae00-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ae00-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ae00-117">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="3ae00-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3ae00-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ae00-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae00-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae00-119">See also</span></span>

- [<span data-ttu-id="3ae00-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="3ae00-120">Metadata Enumerations</span></span>](metadata-enumerations.md)

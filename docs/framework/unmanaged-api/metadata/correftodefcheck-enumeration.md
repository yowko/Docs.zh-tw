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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82abeb0ce3db075d794787bb1fcd5bc18321bef2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093887"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="f6739-102">CorRefToDefCheck 列舉</span><span class="sxs-lookup"><span data-stu-id="f6739-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="f6739-103">指定旗標，以控制哪些參考的項目已轉換成其定義，以便最佳化程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6739-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6739-104">語法</span><span class="sxs-lookup"><span data-stu-id="f6739-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="f6739-105">成員</span><span class="sxs-lookup"><span data-stu-id="f6739-105">Members</span></span>  
  
|<span data-ttu-id="f6739-106">成員</span><span class="sxs-lookup"><span data-stu-id="f6739-106">Member</span></span>|<span data-ttu-id="f6739-107">描述</span><span class="sxs-lookup"><span data-stu-id="f6739-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="f6739-108">指定型別參考和成員的參考，必須定義轉換。</span><span class="sxs-lookup"><span data-stu-id="f6739-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="f6739-109">這是預設值 (`MDTypeRefToDef` &#124; `MDMemberRefToDef`)。</span><span class="sxs-lookup"><span data-stu-id="f6739-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="f6739-110">指定參考的所有項目，必須定義轉換。</span><span class="sxs-lookup"><span data-stu-id="f6739-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="f6739-111">指定沒有參考的項目，必須定義轉換。</span><span class="sxs-lookup"><span data-stu-id="f6739-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="f6739-112">指定只有型別參考，必須轉換型別定義。</span><span class="sxs-lookup"><span data-stu-id="f6739-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="f6739-113">指定只有成員參考，必須定義轉換。</span><span class="sxs-lookup"><span data-stu-id="f6739-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="f6739-114">也就是成員參考應該轉換成方法定義或欄位定義中。</span><span class="sxs-lookup"><span data-stu-id="f6739-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6739-115">需求</span><span class="sxs-lookup"><span data-stu-id="f6739-115">Requirements</span></span>  
 <span data-ttu-id="f6739-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6739-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6739-117">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f6739-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f6739-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6739-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6739-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6739-119">See also</span></span>

- [<span data-ttu-id="f6739-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f6739-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

---
title: "CorRefToDefCheck 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5144cd3ac261647c04ec7e3e27e28618c94fb439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="a3eaa-102">CorRefToDefCheck 列舉</span><span class="sxs-lookup"><span data-stu-id="a3eaa-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="a3eaa-103">指定旗標，以控制哪些參考的項目已轉換成其定義，以便最佳化程式碼。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3eaa-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3eaa-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="a3eaa-105">成員</span><span class="sxs-lookup"><span data-stu-id="a3eaa-105">Members</span></span>  
  
|<span data-ttu-id="a3eaa-106">成員</span><span class="sxs-lookup"><span data-stu-id="a3eaa-106">Member</span></span>|<span data-ttu-id="a3eaa-107">說明</span><span class="sxs-lookup"><span data-stu-id="a3eaa-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="a3eaa-108">指定參考類型和成員參考應該轉換成定義。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="a3eaa-109">這是預設值 (`MDTypeRefToDef` &#124;`MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="a3eaa-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="a3eaa-110">指定應該轉換成定義的所有參考的項目。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="a3eaa-111">指定參考的項目應該將轉換成定義。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="a3eaa-112">指定只有型別參考，應該轉換成的類型定義。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="a3eaa-113">指定只有成員參考，應該轉換成定義。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="a3eaa-114">也就是成員參考應該轉換方法定義或欄位定義。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3eaa-115">需求</span><span class="sxs-lookup"><span data-stu-id="a3eaa-115">Requirements</span></span>  
 <span data-ttu-id="a3eaa-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3eaa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3eaa-117">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a3eaa-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a3eaa-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3eaa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3eaa-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3eaa-119">See Also</span></span>  
 [<span data-ttu-id="a3eaa-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="a3eaa-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

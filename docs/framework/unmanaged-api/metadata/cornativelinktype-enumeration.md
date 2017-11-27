---
title: "CorNativeLinkType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkType
helpviewer_keywords: CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b8da034590bc5e0b2cbd9456d9d5b4ef4970f259
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cornativelinktype-enumeration"></a><span data-ttu-id="9837a-102">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="9837a-102">CorNativeLinkType Enumeration</span></span>
<span data-ttu-id="9837a-103">提供值，這些值表示機器碼中已連結的類型。</span><span class="sxs-lookup"><span data-stu-id="9837a-103">Provides values that indicate the type linked in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9837a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9837a-104">Syntax</span></span>  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a><span data-ttu-id="9837a-105">成員</span><span class="sxs-lookup"><span data-stu-id="9837a-105">Members</span></span>  
  
|<span data-ttu-id="9837a-106">成員</span><span class="sxs-lookup"><span data-stu-id="9837a-106">Member</span></span>|<span data-ttu-id="9837a-107">說明</span><span class="sxs-lookup"><span data-stu-id="9837a-107">Description</span></span>|  
|------------|-----------------|  
|`nltNone`|<span data-ttu-id="9837a-108">表示未指定任何關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9837a-108">Indicates that none of the keywords are specified.</span></span>|  
|`nltAnsi`|<span data-ttu-id="9837a-109">指出指定 ANSI 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9837a-109">Indicates that an ANSI keyword is specified.</span></span>|  
|`nltUnicode`|<span data-ttu-id="9837a-110">指出指定的 Unicode 關鍵字</span><span class="sxs-lookup"><span data-stu-id="9837a-110">Indicates that a Unicode keyword is specified</span></span>|  
|`nltAuto`|<span data-ttu-id="9837a-111">指出指定 auto 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9837a-111">Indicates that an auto keyword is specified.</span></span>|  
|`nltOle`|<span data-ttu-id="9837a-112">指出指定之 OLE 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9837a-112">Indicates that an OLE keyword is specified.</span></span>|  
|`nltMaxValue`|<span data-ttu-id="9837a-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="9837a-113">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9837a-114">需求</span><span class="sxs-lookup"><span data-stu-id="9837a-114">Requirements</span></span>  
 <span data-ttu-id="9837a-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9837a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9837a-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9837a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9837a-117">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9837a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9837a-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9837a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9837a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9837a-119">See Also</span></span>  
 [<span data-ttu-id="9837a-120">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="9837a-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

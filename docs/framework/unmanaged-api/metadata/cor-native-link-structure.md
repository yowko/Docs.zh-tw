---
title: "COR_NATIVE_LINK 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_NATIVE_LINK
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_NATIVE_LINK
helpviewer_keywords: COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e27b66fce8a78ef0feb7ed10e77cc51fc1fe83c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="bd852-102">COR_NATIVE_LINK 結構</span><span class="sxs-lookup"><span data-stu-id="bd852-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="bd852-103">包含用來連結原生程式碼的資訊。</span><span class="sxs-lookup"><span data-stu-id="bd852-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd852-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd852-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="bd852-105">成員</span><span class="sxs-lookup"><span data-stu-id="bd852-105">Members</span></span>  
  
|<span data-ttu-id="bd852-106">成員</span><span class="sxs-lookup"><span data-stu-id="bd852-106">Member</span></span>|<span data-ttu-id="bd852-107">說明</span><span class="sxs-lookup"><span data-stu-id="bd852-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="bd852-108">要連結原生程式碼的類型。</span><span class="sxs-lookup"><span data-stu-id="bd852-108">The type to be linked in native code.</span></span> <span data-ttu-id="bd852-109">這個值是其中一個[CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="bd852-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="bd852-110">連結器在連結機器碼時使用的旗標。</span><span class="sxs-lookup"><span data-stu-id="bd852-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="bd852-111">這個值是其中一個[CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="bd852-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="bd852-112">MemberRef 中繼資料語彙基元所代表的進入點。</span><span class="sxs-lookup"><span data-stu-id="bd852-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="bd852-113">格式是`lib:entrypoint`。</span><span class="sxs-lookup"><span data-stu-id="bd852-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bd852-114">需求</span><span class="sxs-lookup"><span data-stu-id="bd852-114">Requirements</span></span>  
 <span data-ttu-id="bd852-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd852-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd852-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd852-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd852-117">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bd852-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd852-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd852-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd852-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd852-119">See Also</span></span>  
 [<span data-ttu-id="bd852-120">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="bd852-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="bd852-121">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="bd852-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="bd852-122">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="bd852-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)

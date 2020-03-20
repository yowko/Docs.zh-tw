---
title: COR_NATIVE_LINK 結構
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177951"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="f3f7a-102">COR_NATIVE_LINK 結構</span><span class="sxs-lookup"><span data-stu-id="f3f7a-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="f3f7a-103">包含用來連結原生程式碼的資訊。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3f7a-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="f3f7a-105">成員</span><span class="sxs-lookup"><span data-stu-id="f3f7a-105">Members</span></span>  
  
|<span data-ttu-id="f3f7a-106">member</span><span class="sxs-lookup"><span data-stu-id="f3f7a-106">Member</span></span>|<span data-ttu-id="f3f7a-107">描述</span><span class="sxs-lookup"><span data-stu-id="f3f7a-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="f3f7a-108">要在本機代碼中連結的類型。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-108">The type to be linked in native code.</span></span> <span data-ttu-id="f3f7a-109">此值是[CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)值之一。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="f3f7a-110">連結器在連結本機代碼時使用的標誌。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="f3f7a-111">此值是[CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)值之一。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="f3f7a-112">表示進入點的會員Ref 中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="f3f7a-113">格式為 `lib:entrypoint`。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3f7a-114">需求</span><span class="sxs-lookup"><span data-stu-id="f3f7a-114">Requirements</span></span>  
 <span data-ttu-id="f3f7a-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3f7a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3f7a-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="f3f7a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3f7a-117">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f3f7a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3f7a-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3f7a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f7a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3f7a-119">See also</span></span>

- [<span data-ttu-id="f3f7a-120">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="f3f7a-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f3f7a-121">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="f3f7a-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="f3f7a-122">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="f3f7a-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)

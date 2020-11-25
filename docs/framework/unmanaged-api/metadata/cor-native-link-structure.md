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
ms.openlocfilehash: 15f573ebc07bcf08a1ab8f5a5bbb88e940c5c8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724165"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="f2e4b-102">COR_NATIVE_LINK 結構</span><span class="sxs-lookup"><span data-stu-id="f2e4b-102">COR_NATIVE_LINK Structure</span></span>

<span data-ttu-id="f2e4b-103">包含用來連結原生程式碼的資訊。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2e4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2e4b-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="f2e4b-105">成員</span><span class="sxs-lookup"><span data-stu-id="f2e4b-105">Members</span></span>  
  
|<span data-ttu-id="f2e4b-106">member</span><span class="sxs-lookup"><span data-stu-id="f2e4b-106">Member</span></span>|<span data-ttu-id="f2e4b-107">描述</span><span class="sxs-lookup"><span data-stu-id="f2e4b-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="f2e4b-108">要在原生程式碼中連結的型別。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-108">The type to be linked in native code.</span></span> <span data-ttu-id="f2e4b-109">此值是其中一個 [CorNativeLinkType](cornativelinktype-enumeration.md) 值。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="f2e4b-110">連結器連結機器碼時，連結器所使用的旗標。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="f2e4b-111">此值是其中一個 [CorNativeLinkFlags](cornativelinkflags-enumeration.md) 值。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="f2e4b-112">代表進入點的 MemberRef 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="f2e4b-113">格式為 `lib:entrypoint`。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2e4b-114">需求</span><span class="sxs-lookup"><span data-stu-id="f2e4b-114">Requirements</span></span>  

 <span data-ttu-id="f2e4b-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e4b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2e4b-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f2e4b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2e4b-117">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f2e4b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2e4b-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2e4b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e4b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2e4b-119">See also</span></span>

- [<span data-ttu-id="f2e4b-120">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="f2e4b-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="f2e4b-121">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="f2e4b-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="f2e4b-122">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="f2e4b-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)

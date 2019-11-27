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
ms.openlocfilehash: d03c22c455f0e44ce32d4593d9eee50ceef94a22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443954"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="53f27-102">COR_NATIVE_LINK 結構</span><span class="sxs-lookup"><span data-stu-id="53f27-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="53f27-103">包含用來連結原生程式碼的資訊。</span><span class="sxs-lookup"><span data-stu-id="53f27-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53f27-104">語法</span><span class="sxs-lookup"><span data-stu-id="53f27-104">Syntax</span></span>  
  
```cpp  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="53f27-105">Members</span><span class="sxs-lookup"><span data-stu-id="53f27-105">Members</span></span>  
  
|<span data-ttu-id="53f27-106">成員</span><span class="sxs-lookup"><span data-stu-id="53f27-106">Member</span></span>|<span data-ttu-id="53f27-107">描述</span><span class="sxs-lookup"><span data-stu-id="53f27-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="53f27-108">要以機器碼連結的類型。</span><span class="sxs-lookup"><span data-stu-id="53f27-108">The type to be linked in native code.</span></span> <span data-ttu-id="53f27-109">這個值是其中一個[CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="53f27-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="53f27-110">連結器在連結機器碼時所使用的旗標。</span><span class="sxs-lookup"><span data-stu-id="53f27-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="53f27-111">這個值是其中一個[CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="53f27-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="53f27-112">表示進入點的 MemberRef 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="53f27-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="53f27-113">格式為 `lib:entrypoint`。</span><span class="sxs-lookup"><span data-stu-id="53f27-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53f27-114">需求</span><span class="sxs-lookup"><span data-stu-id="53f27-114">Requirements</span></span>  
 <span data-ttu-id="53f27-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53f27-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53f27-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="53f27-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53f27-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="53f27-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="53f27-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53f27-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f27-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="53f27-119">See also</span></span>

- [<span data-ttu-id="53f27-120">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="53f27-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="53f27-121">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="53f27-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="53f27-122">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="53f27-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)

---
title: CorDebugGuidToTypeMapping 結構
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
ms.openlocfilehash: b855a53c9e4303138d7605bdf108d37bb345b917
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789334"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="c1170-102">CorDebugGuidToTypeMapping 結構</span><span class="sxs-lookup"><span data-stu-id="c1170-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="c1170-103">將 Windows 執行階段的 GUID 對應至其相對應的 ICorDebugType 物件。</span><span class="sxs-lookup"><span data-stu-id="c1170-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1170-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1170-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="c1170-105">Members</span><span class="sxs-lookup"><span data-stu-id="c1170-105">Members</span></span>  
  
|<span data-ttu-id="c1170-106">成員</span><span class="sxs-lookup"><span data-stu-id="c1170-106">Member</span></span>|<span data-ttu-id="c1170-107">描述</span><span class="sxs-lookup"><span data-stu-id="c1170-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="c1170-108">快取 Windows 執行階段類型的 GUID。</span><span class="sxs-lookup"><span data-stu-id="c1170-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="c1170-109">ICorDebugType 物件的指標，提供快取類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c1170-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1170-110">需求</span><span class="sxs-lookup"><span data-stu-id="c1170-110">Requirements</span></span>  
 <span data-ttu-id="c1170-111">**平臺：** Windows 執行階段。</span><span class="sxs-lookup"><span data-stu-id="c1170-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="c1170-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1170-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1170-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1170-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1170-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1170-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1170-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1170-115">See also</span></span>

- [<span data-ttu-id="c1170-116">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="c1170-116">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c1170-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="c1170-117">Debugging</span></span>](index.md)

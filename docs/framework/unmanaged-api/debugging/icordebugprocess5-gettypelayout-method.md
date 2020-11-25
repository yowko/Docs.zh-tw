---
title: ICorDebugProcess5::GetTypeLayout 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 32277e8adcd4bb08c8d0480eb3b4e7e4b5949479
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723125"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="e4a67-102">ICorDebugProcess5::GetTypeLayout 方法</span><span class="sxs-lookup"><span data-stu-id="e4a67-102">ICorDebugProcess5::GetTypeLayout Method</span></span>

<span data-ttu-id="e4a67-103">根據物件的類型識別碼，取得記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4a67-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a67-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4a67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4a67-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4a67-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="e4a67-106">在 [COR_TYPEID](cor-typeid-structure.md) 權杖，指定需要其配置的類型。</span><span class="sxs-lookup"><span data-stu-id="e4a67-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="e4a67-107">擴展 [COR_TYPE_LAYOUT](cor-type-layout-structure.md) 結構的指標，其中包含記憶體中物件配置的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4a67-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4a67-108">備註</span><span class="sxs-lookup"><span data-stu-id="e4a67-108">Remarks</span></span>  

 <span data-ttu-id="e4a67-109">`ICorDebugProcess5::GetTypeLayout`方法會根據物件的[COR_TYPEID](cor-typeid-structure.md)（由一些其他[ICorDebugProcess5](icordebugprocess5-interface.md)方法所傳回）來提供物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4a67-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="e4a67-110">這項資訊是由方法所填入的 [COR_TYPE_LAYOUT](cor-type-layout-structure.md) 結構所提供。</span><span class="sxs-lookup"><span data-stu-id="e4a67-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4a67-111">需求</span><span class="sxs-lookup"><span data-stu-id="e4a67-111">Requirements</span></span>  

 <span data-ttu-id="e4a67-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4a67-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4a67-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4a67-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4a67-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4a67-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4a67-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4a67-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a67-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4a67-116">See also</span></span>

- [<span data-ttu-id="e4a67-117">COR_TYPE_LAYOUT 結構</span><span class="sxs-lookup"><span data-stu-id="e4a67-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="e4a67-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="e4a67-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="e4a67-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e4a67-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: ICorDebugType2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 878941f7af71fa5e3de8e38c4a68a66cb964983d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223156"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="a0527-102">ICorDebugType2 介面</span><span class="sxs-lookup"><span data-stu-id="a0527-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="a0527-103">可擴充 ICorDebugType 介面來擷取基底型別或複雜的 （使用者定義） 型別的型別識別項。</span><span class="sxs-lookup"><span data-stu-id="a0527-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0527-104">方法</span><span class="sxs-lookup"><span data-stu-id="a0527-104">Methods</span></span>  
  
|<span data-ttu-id="a0527-105">方法</span><span class="sxs-lookup"><span data-stu-id="a0527-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="a0527-106">GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="a0527-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="a0527-107">取得[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)這種類型。</span><span class="sxs-lookup"><span data-stu-id="a0527-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0527-108">備註</span><span class="sxs-lookup"><span data-stu-id="a0527-108">Remarks</span></span>  
 <span data-ttu-id="a0527-109">這個介面是 ICorDebugType 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="a0527-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0527-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a0527-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0527-111">範例</span><span class="sxs-lookup"><span data-stu-id="a0527-111">Example</span></span>  
 <span data-ttu-id="a0527-112">下列程式碼片段說明如何使用[ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a0527-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="a0527-113">需求</span><span class="sxs-lookup"><span data-stu-id="a0527-113">Requirements</span></span>  
 <span data-ttu-id="a0527-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0527-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0527-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0527-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0527-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0527-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a0527-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="a0527-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0527-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0527-118">See also</span></span>

- [<span data-ttu-id="a0527-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a0527-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

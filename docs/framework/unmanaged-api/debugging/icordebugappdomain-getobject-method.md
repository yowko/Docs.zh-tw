---
title: ICorDebugAppDomain::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: a163667ea7eca1ed817d642efdb8fc4efa2a0651
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676058"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="4efc5-102">ICorDebugAppDomain::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="4efc5-102">ICorDebugAppDomain::GetObject Method</span></span>

<span data-ttu-id="4efc5-103">取得 common language runtime (CLR) 應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="4efc5-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4efc5-104">語法</span><span class="sxs-lookup"><span data-stu-id="4efc5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4efc5-105">參數</span><span class="sxs-lookup"><span data-stu-id="4efc5-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="4efc5-106">擴展ICorDebugValue 介面物件位址的指標，該物件代表 CLR 應用程式域。</span><span class="sxs-lookup"><span data-stu-id="4efc5-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4efc5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4efc5-107">Return Value</span></span>  

 <span data-ttu-id="4efc5-108">如果 <xref:System.AppDomain?displayProperty=nameWithType> 尚未針對這個應用程式域來建立 managed 物件，則方法會傳回 `S_FALSE` 並放 `NULL` 入 `*ppObject` 。</span><span class="sxs-lookup"><span data-stu-id="4efc5-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4efc5-109">備註</span><span class="sxs-lookup"><span data-stu-id="4efc5-109">Remarks</span></span>  

 <span data-ttu-id="4efc5-110">進程中的每個應用程式域在執行時間中可能會有 <xref:System.AppDomain?displayProperty=nameWithType> 代表它的 managed 物件。</span><span class="sxs-lookup"><span data-stu-id="4efc5-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="4efc5-111">此函式會取得對應至此 managed 物件的 ICorDebugValue 介面物件 <xref:System.AppDomain?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="4efc5-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4efc5-112">需求</span><span class="sxs-lookup"><span data-stu-id="4efc5-112">Requirements</span></span>  

 <span data-ttu-id="4efc5-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4efc5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4efc5-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4efc5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4efc5-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4efc5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4efc5-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4efc5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

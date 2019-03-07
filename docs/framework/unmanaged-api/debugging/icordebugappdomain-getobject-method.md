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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ca9792df69f859e20f1d9e40754d1cec138945d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480022"
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="c26b1-102">ICorDebugAppDomain::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="c26b1-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="c26b1-103">Common language runtime (CLR) 應用程式定義域中取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="c26b1-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c26b1-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c26b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="c26b1-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="c26b1-106">[out]ICorDebugValue 介面物件，表示 CLR 應用程式定義域的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c26b1-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c26b1-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c26b1-107">Return Value</span></span>  
 <span data-ttu-id="c26b1-108">如果 managed<xref:System.AppDomain?displayProperty=nameWithType>尚未針對這個應用程式定義域已建構物件，此方法會傳回`S_FALSE`，並將放`NULL`在`*ppObject`。</span><span class="sxs-lookup"><span data-stu-id="c26b1-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c26b1-109">備註</span><span class="sxs-lookup"><span data-stu-id="c26b1-109">Remarks</span></span>  
 <span data-ttu-id="c26b1-110">每個應用程式定義域的處理序中可能有 managed<xref:System.AppDomain?displayProperty=nameWithType>表示該執行階段中的物件。</span><span class="sxs-lookup"><span data-stu-id="c26b1-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="c26b1-111">此函式取得 ICorDebugValue 介面物件，對應至這個受控<xref:System.AppDomain?displayProperty=nameWithType>物件。</span><span class="sxs-lookup"><span data-stu-id="c26b1-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26b1-112">需求</span><span class="sxs-lookup"><span data-stu-id="c26b1-112">Requirements</span></span>  
 <span data-ttu-id="c26b1-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c26b1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26b1-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c26b1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c26b1-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c26b1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c26b1-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26b1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

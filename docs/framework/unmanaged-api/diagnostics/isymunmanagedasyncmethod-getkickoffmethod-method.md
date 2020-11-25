---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: 2d4515087812b2b7c9303228ac5e5bbf34e8aa91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707187"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="9759d-102">ISymUnmanagedAsyncMethod::GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="9759d-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>

<span data-ttu-id="9759d-103">請參閱 [DefineKickoffMethod 方法](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9759d-103">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9759d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9759d-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9759d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9759d-105">Parameters</span></span>  
  
|<span data-ttu-id="9759d-106">參數</span><span class="sxs-lookup"><span data-stu-id="9759d-106">Parameter</span></span>|<span data-ttu-id="9759d-107">描述</span><span class="sxs-lookup"><span data-stu-id="9759d-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="9759d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9759d-108">Return Value</span></span>  

 <span data-ttu-id="9759d-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="9759d-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9759d-110">需求</span><span class="sxs-lookup"><span data-stu-id="9759d-110">Requirements</span></span>  

 <span data-ttu-id="9759d-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="9759d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9759d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9759d-112">See also</span></span>

- [<span data-ttu-id="9759d-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="9759d-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)

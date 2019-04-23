---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod 方法
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599d41336778db8ce8dcf3ac567e4e2cc8833e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174937"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="45fa6-102">ISymUnmanagedAsyncMethod::GetKickoffMethod 方法</span><span class="sxs-lookup"><span data-stu-id="45fa6-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="45fa6-103">請參閱[DefineKickoffMethod 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)。</span><span class="sxs-lookup"><span data-stu-id="45fa6-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45fa6-104">語法</span><span class="sxs-lookup"><span data-stu-id="45fa6-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45fa6-105">參數</span><span class="sxs-lookup"><span data-stu-id="45fa6-105">Parameters</span></span>  
  
|<span data-ttu-id="45fa6-106">參數</span><span class="sxs-lookup"><span data-stu-id="45fa6-106">Parameter</span></span>|<span data-ttu-id="45fa6-107">描述</span><span class="sxs-lookup"><span data-stu-id="45fa6-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="45fa6-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="45fa6-108">Return Value</span></span>  
 <span data-ttu-id="45fa6-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="45fa6-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45fa6-110">需求</span><span class="sxs-lookup"><span data-stu-id="45fa6-110">Requirements</span></span>  
 <span data-ttu-id="45fa6-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="45fa6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45fa6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45fa6-112">See also</span></span>

- [<span data-ttu-id="45fa6-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="45fa6-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)

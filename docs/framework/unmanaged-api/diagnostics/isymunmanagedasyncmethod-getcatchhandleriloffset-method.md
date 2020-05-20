---
title: ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
ms.openlocfilehash: f45b9a53909ab23428a8d51be2e672bfdd15d951
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441847"
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="bf13d-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="bf13d-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="bf13d-103">請參閱[DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="bf13d-103">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf13d-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf13d-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf13d-105">參數</span><span class="sxs-lookup"><span data-stu-id="bf13d-105">Parameters</span></span>  
  
|<span data-ttu-id="bf13d-106">參數</span><span class="sxs-lookup"><span data-stu-id="bf13d-106">Parameter</span></span>|<span data-ttu-id="bf13d-107">說明</span><span class="sxs-lookup"><span data-stu-id="bf13d-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="bf13d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="bf13d-108">Return Value</span></span>  
 <span data-ttu-id="bf13d-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="bf13d-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf13d-110">需求</span><span class="sxs-lookup"><span data-stu-id="bf13d-110">Requirements</span></span>  
 <span data-ttu-id="bf13d-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bf13d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf13d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf13d-112">See also</span></span>

- [<span data-ttu-id="bf13d-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="bf13d-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)

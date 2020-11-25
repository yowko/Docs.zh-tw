---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod 方法
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: af02aba1a0d390c103e8c6108f90b93fe2a98ff3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707148"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="f1c5b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod 方法</span><span class="sxs-lookup"><span data-stu-id="f1c5b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>

<span data-ttu-id="f1c5b-103">檢查方法是否有非同步資訊。</span><span class="sxs-lookup"><span data-stu-id="f1c5b-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="f1c5b-104">如果這個方法傳回，則 `FALSE` 呼叫此介面中的任何其他方法是不正確。</span><span class="sxs-lookup"><span data-stu-id="f1c5b-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="f1c5b-105">`E_UNEXPECTED`在此情況下，它們全都會傳回。</span><span class="sxs-lookup"><span data-stu-id="f1c5b-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1c5b-106">語法</span><span class="sxs-lookup"><span data-stu-id="f1c5b-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1c5b-107">參數</span><span class="sxs-lookup"><span data-stu-id="f1c5b-107">Parameters</span></span>  
  
|<span data-ttu-id="f1c5b-108">參數</span><span class="sxs-lookup"><span data-stu-id="f1c5b-108">Parameter</span></span>|<span data-ttu-id="f1c5b-109">描述</span><span class="sxs-lookup"><span data-stu-id="f1c5b-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="f1c5b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f1c5b-110">Return Value</span></span>  

 <span data-ttu-id="f1c5b-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="f1c5b-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1c5b-112">需求</span><span class="sxs-lookup"><span data-stu-id="f1c5b-112">Requirements</span></span>  

 <span data-ttu-id="f1c5b-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="f1c5b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c5b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1c5b-114">See also</span></span>

- [<span data-ttu-id="f1c5b-115">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="f1c5b-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)

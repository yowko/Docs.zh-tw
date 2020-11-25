---
title: ISymUnmanagedMethod::GetParameters 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: c66fd810ae4976bc0b5e04572b899465cebe4bbb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699504"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="4b515-102">ISymUnmanagedMethod::GetParameters 方法</span><span class="sxs-lookup"><span data-stu-id="4b515-102">ISymUnmanagedMethod::GetParameters Method</span></span>

<span data-ttu-id="4b515-103">取得這個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="4b515-103">Gets the parameters for this method.</span></span> <span data-ttu-id="4b515-104">參數會依照其在方法簽章中的定義順序傳回。</span><span class="sxs-lookup"><span data-stu-id="4b515-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b515-105">語法</span><span class="sxs-lookup"><span data-stu-id="4b515-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b515-106">參數</span><span class="sxs-lookup"><span data-stu-id="4b515-106">Parameters</span></span>  

 `cParams`  
 <span data-ttu-id="4b515-107">[in] `params` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="4b515-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="4b515-108">在的指標 `ULONG32` ，會接收包含參數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="4b515-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="4b515-109">擴展接收參數之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="4b515-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b515-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b515-110">Return Value</span></span>  

 <span data-ttu-id="4b515-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4b515-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b515-112">需求</span><span class="sxs-lookup"><span data-stu-id="4b515-112">Requirements</span></span>  

 <span data-ttu-id="4b515-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="4b515-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b515-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b515-114">See also</span></span>

- [<span data-ttu-id="4b515-115">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="4b515-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)

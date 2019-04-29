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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a757e3b28a94c96e28a5bab736a6820a83617a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939629"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="41e47-102">ISymUnmanagedMethod::GetParameters 方法</span><span class="sxs-lookup"><span data-stu-id="41e47-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="41e47-103">取得這個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="41e47-103">Gets the parameters for this method.</span></span> <span data-ttu-id="41e47-104">參數會傳回方法的簽章中定義的順序。</span><span class="sxs-lookup"><span data-stu-id="41e47-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e47-105">語法</span><span class="sxs-lookup"><span data-stu-id="41e47-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e47-106">參數</span><span class="sxs-lookup"><span data-stu-id="41e47-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="41e47-107">[in] `params` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="41e47-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="41e47-108">[in]指標`ULONG32`接收，才可包含參數的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="41e47-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="41e47-109">[out]接收的參數緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="41e47-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41e47-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="41e47-110">Return Value</span></span>  
 <span data-ttu-id="41e47-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="41e47-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e47-112">需求</span><span class="sxs-lookup"><span data-stu-id="41e47-112">Requirements</span></span>  
 <span data-ttu-id="41e47-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="41e47-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e47-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e47-114">See also</span></span>

- [<span data-ttu-id="41e47-115">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="41e47-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

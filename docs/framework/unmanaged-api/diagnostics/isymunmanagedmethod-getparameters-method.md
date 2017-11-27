---
title: "ISymUnmanagedMethod::GetParameters 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetParameters
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 057cafc5270eeb82b4c9b9becac59ea45ea21371
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="aa372-102">ISymUnmanagedMethod::GetParameters 方法</span><span class="sxs-lookup"><span data-stu-id="aa372-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="aa372-103">取得這個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="aa372-103">Gets the parameters for this method.</span></span> <span data-ttu-id="aa372-104">參數會傳回方法的簽章中所定義的順序。</span><span class="sxs-lookup"><span data-stu-id="aa372-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa372-105">語法</span><span class="sxs-lookup"><span data-stu-id="aa372-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa372-106">參數</span><span class="sxs-lookup"><span data-stu-id="aa372-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="aa372-107">[in] `params` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="aa372-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="aa372-108">[in]指標`ULONG32`包含參數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="aa372-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="aa372-109">[out]接收參數緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="aa372-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa372-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="aa372-110">Return Value</span></span>  
 <span data-ttu-id="aa372-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="aa372-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa372-112">需求</span><span class="sxs-lookup"><span data-stu-id="aa372-112">Requirements</span></span>  
 <span data-ttu-id="aa372-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aa372-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa372-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa372-114">See Also</span></span>  
 [<span data-ttu-id="aa372-115">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="aa372-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

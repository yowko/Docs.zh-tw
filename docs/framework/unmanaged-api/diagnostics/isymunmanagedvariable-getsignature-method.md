---
title: "ISymUnmanagedVariable::GetSignature 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetSignature
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1e29cd4a38e9abbe380b51b81fc2849b833d87e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="49909-102">ISymUnmanagedVariable::GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="49909-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="49909-103">取得這個變數的簽章。</span><span class="sxs-lookup"><span data-stu-id="49909-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49909-104">語法</span><span class="sxs-lookup"><span data-stu-id="49909-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49909-105">參數</span><span class="sxs-lookup"><span data-stu-id="49909-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="49909-106">[in]所指向之緩衝區的長度`sig`參數。</span><span class="sxs-lookup"><span data-stu-id="49909-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="49909-107">[out]指標`ULONG32`接收以字元為單位，以包含簽章所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="49909-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="49909-108">[out]儲存簽章的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="49909-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49909-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="49909-109">Return Value</span></span>  
 <span data-ttu-id="49909-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="49909-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49909-111">需求</span><span class="sxs-lookup"><span data-stu-id="49909-111">Requirements</span></span>  
 <span data-ttu-id="49909-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="49909-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49909-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49909-113">See Also</span></span>  
 [<span data-ttu-id="49909-114">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="49909-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

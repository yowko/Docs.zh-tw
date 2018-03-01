---
title: "ISymUnmanagedConstant::GetSignature 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10bdf7b8b83b56ff856d966d2764ed04e06090aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="b553a-102">ISymUnmanagedConstant::GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="b553a-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="b553a-103">取得常數的簽章。</span><span class="sxs-lookup"><span data-stu-id="b553a-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b553a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b553a-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b553a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b553a-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="b553a-106">[in]緩衝區的長度，`pcSig`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="b553a-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="b553a-107">[out]指標`ULONG32`接收以字元為單位，以包含簽章所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="b553a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="b553a-108">[out]儲存簽章的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b553a-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b553a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b553a-109">Return Value</span></span>  
 <span data-ttu-id="b553a-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b553a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b553a-111">需求</span><span class="sxs-lookup"><span data-stu-id="b553a-111">Requirements</span></span>  
 <span data-ttu-id="b553a-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b553a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b553a-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="b553a-113">See Also</span></span>  
 [<span data-ttu-id="b553a-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="b553a-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="b553a-115">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="b553a-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="b553a-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="b553a-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)

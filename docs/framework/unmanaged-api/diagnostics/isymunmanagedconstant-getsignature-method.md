---
title: ISymUnmanagedConstant::GetSignature 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce9ce768e32434e0a1acd2fad67a0cdc99f49e18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430142"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="27ab6-102">ISymUnmanagedConstant::GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="27ab6-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="27ab6-103">取得常數的簽章。</span><span class="sxs-lookup"><span data-stu-id="27ab6-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27ab6-104">語法</span><span class="sxs-lookup"><span data-stu-id="27ab6-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27ab6-105">參數</span><span class="sxs-lookup"><span data-stu-id="27ab6-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="27ab6-106">[in]緩衝區的長度，`pcSig`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="27ab6-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="27ab6-107">[out]指標`ULONG32`接收以字元為單位，以包含簽章所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="27ab6-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="27ab6-108">[out]儲存簽章的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="27ab6-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27ab6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="27ab6-109">Return Value</span></span>  
 <span data-ttu-id="27ab6-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="27ab6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27ab6-111">需求</span><span class="sxs-lookup"><span data-stu-id="27ab6-111">Requirements</span></span>  
 <span data-ttu-id="27ab6-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27ab6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ab6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27ab6-113">See Also</span></span>  
 [<span data-ttu-id="27ab6-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="27ab6-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="27ab6-115">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="27ab6-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="27ab6-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="27ab6-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)

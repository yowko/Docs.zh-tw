---
title: ISymUnmanagedVariable::GetSignature 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abd4bb00f5c1e703740462f1709407616ac8a8e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778236"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="39136-102">ISymUnmanagedVariable::GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="39136-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="39136-103">取得這個變數的簽章。</span><span class="sxs-lookup"><span data-stu-id="39136-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39136-104">語法</span><span class="sxs-lookup"><span data-stu-id="39136-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39136-105">參數</span><span class="sxs-lookup"><span data-stu-id="39136-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="39136-106">[in]所指向緩衝區的長度`sig`參數。</span><span class="sxs-lookup"><span data-stu-id="39136-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="39136-107">[out]指標`ULONG32`接收大小，以字元為單位，以包含簽章所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="39136-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="39136-108">[out]儲存簽章的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="39136-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39136-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="39136-109">Return Value</span></span>  
 <span data-ttu-id="39136-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="39136-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39136-111">需求</span><span class="sxs-lookup"><span data-stu-id="39136-111">Requirements</span></span>  
 <span data-ttu-id="39136-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="39136-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39136-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39136-113">See also</span></span>

- [<span data-ttu-id="39136-114">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="39136-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

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
ms.openlocfilehash: 4436e4528c1dc486eb5c443c5a9467ac69a26c7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706927"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="c6ae1-102">ISymUnmanagedConstant::GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="c6ae1-102">ISymUnmanagedConstant::GetSignature Method</span></span>

<span data-ttu-id="c6ae1-103">取得常數的簽章。</span><span class="sxs-lookup"><span data-stu-id="c6ae1-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ae1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6ae1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6ae1-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6ae1-105">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="c6ae1-106">在參數所指向的緩衝區長度 `pcSig` 。</span><span class="sxs-lookup"><span data-stu-id="c6ae1-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="c6ae1-107">擴展的指標， `ULONG32` 會接收包含簽章所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="c6ae1-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="c6ae1-108">擴展儲存簽章的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c6ae1-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6ae1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c6ae1-109">Return Value</span></span>  

 <span data-ttu-id="c6ae1-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c6ae1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ae1-111">需求</span><span class="sxs-lookup"><span data-stu-id="c6ae1-111">Requirements</span></span>  

 <span data-ttu-id="c6ae1-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c6ae1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ae1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6ae1-113">See also</span></span>

- [<span data-ttu-id="c6ae1-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="c6ae1-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="c6ae1-115">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="c6ae1-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="c6ae1-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="c6ae1-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)

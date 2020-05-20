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
ms.openlocfilehash: 332d60418c744a9391c7c0afc20248c2239b090c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441616"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="27b4d-102">ISymUnmanagedConstant::GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="27b4d-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="27b4d-103">取得常數的簽章。</span><span class="sxs-lookup"><span data-stu-id="27b4d-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27b4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="27b4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27b4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="27b4d-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="27b4d-106">在參數所指向之緩衝區的長度 `pcSig` 。</span><span class="sxs-lookup"><span data-stu-id="27b4d-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="27b4d-107">脫銷的指標， `ULONG32` 接收包含簽章所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="27b4d-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="27b4d-108">脫銷儲存簽章的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="27b4d-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27b4d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="27b4d-109">Return Value</span></span>  
 <span data-ttu-id="27b4d-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="27b4d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27b4d-111">需求</span><span class="sxs-lookup"><span data-stu-id="27b4d-111">Requirements</span></span>  
 <span data-ttu-id="27b4d-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="27b4d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b4d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27b4d-113">See also</span></span>

- [<span data-ttu-id="27b4d-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="27b4d-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="27b4d-115">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="27b4d-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="27b4d-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="27b4d-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)

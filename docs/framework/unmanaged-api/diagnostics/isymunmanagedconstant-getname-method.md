---
title: ISymUnmanagedConstant::GetName 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1da8d89cf9ae2eed7b846774434d6ea472afbb94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939967"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="5a4da-102">ISymUnmanagedConstant::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="5a4da-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="5a4da-103">取得常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a4da-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4da-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a4da-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a4da-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a4da-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5a4da-106">[in]緩衝區的長度，`szName`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="5a4da-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5a4da-107">[out]指標`ULONG32`接收大小，以字元為單位，以存放的名稱，包括 null 終止的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5a4da-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="5a4da-108">[out]儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5a4da-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a4da-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5a4da-109">Return Value</span></span>  
 <span data-ttu-id="5a4da-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a4da-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4da-111">需求</span><span class="sxs-lookup"><span data-stu-id="5a4da-111">Requirements</span></span>  
 <span data-ttu-id="5a4da-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a4da-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4da-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a4da-113">See also</span></span>

- [<span data-ttu-id="5a4da-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="5a4da-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="5a4da-115">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="5a4da-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="5a4da-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="5a4da-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)

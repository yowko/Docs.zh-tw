---
title: "ISymUnmanagedConstant::GetName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedConstant.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b6dc3eb79f351041687586327e4e095225acf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="9db9b-102">ISymUnmanagedConstant::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="9db9b-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="9db9b-103">取得常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="9db9b-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9db9b-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9db9b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9db9b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9db9b-106">[in]緩衝區的長度，`szName`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="9db9b-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9db9b-107">[out]指標`ULONG32`接收以字元為單位，以包含檔案的名稱，包括 null 結束所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="9db9b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="9db9b-108">[out]儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9db9b-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9db9b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9db9b-109">Return Value</span></span>  
 <span data-ttu-id="9db9b-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="9db9b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db9b-111">需求</span><span class="sxs-lookup"><span data-stu-id="9db9b-111">Requirements</span></span>  
 <span data-ttu-id="9db9b-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9db9b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db9b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9db9b-113">See Also</span></span>  
 [<span data-ttu-id="9db9b-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="9db9b-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="9db9b-115">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="9db9b-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="9db9b-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="9db9b-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)

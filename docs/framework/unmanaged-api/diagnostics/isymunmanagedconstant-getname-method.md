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
ms.workload: dotnet
ms.openlocfilehash: d312329a2e59376c94937cf3d9bc08a8e6e0e862
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="3bdb2-102">ISymUnmanagedConstant::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="3bdb2-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="3bdb2-103">取得常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="3bdb2-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bdb2-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bdb2-105">參數</span><span class="sxs-lookup"><span data-stu-id="3bdb2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3bdb2-106">[in]緩衝區的長度，`szName`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="3bdb2-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3bdb2-107">[out]指標`ULONG32`接收以字元為單位，以包含檔案的名稱，包括 null 結束所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="3bdb2-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="3bdb2-108">[out]儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3bdb2-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bdb2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3bdb2-109">Return Value</span></span>  
 <span data-ttu-id="3bdb2-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="3bdb2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bdb2-111">需求</span><span class="sxs-lookup"><span data-stu-id="3bdb2-111">Requirements</span></span>  
 <span data-ttu-id="3bdb2-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3bdb2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdb2-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3bdb2-113">See Also</span></span>  
 [<span data-ttu-id="3bdb2-114">ISymUnmanagedConstant 介面</span><span class="sxs-lookup"><span data-stu-id="3bdb2-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="3bdb2-115">GetSignature 方法</span><span class="sxs-lookup"><span data-stu-id="3bdb2-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="3bdb2-116">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="3bdb2-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)

---
title: "ISymUnmanagedMethod::GetToken 方法"
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
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bfdc070c21c7929166bfa957c0e0dd63da80f761
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="31b31-102">ISymUnmanagedMethod::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="31b31-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="31b31-103">傳回這個方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="31b31-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b31-104">語法</span><span class="sxs-lookup"><span data-stu-id="31b31-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31b31-105">參數</span><span class="sxs-lookup"><span data-stu-id="31b31-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="31b31-106">[out]指標`mdMethodDef`接收以字元為單位，以包含中繼資料所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="31b31-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31b31-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="31b31-107">Return Value</span></span>  
 <span data-ttu-id="31b31-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="31b31-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31b31-109">需求</span><span class="sxs-lookup"><span data-stu-id="31b31-109">Requirements</span></span>  
 <span data-ttu-id="31b31-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31b31-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b31-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="31b31-111">See Also</span></span>  
 [<span data-ttu-id="31b31-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="31b31-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

---
title: ISymUnmanagedScope2::GetConstants 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08bc85c7a5b53c145375ca34f11ec499e5e7528f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761581"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="fc2a3-102">ISymUnmanagedScope2::GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="fc2a3-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="fc2a3-103">取得此範圍內定義的區域常數。</span><span class="sxs-lookup"><span data-stu-id="fc2a3-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc2a3-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc2a3-105">參數</span><span class="sxs-lookup"><span data-stu-id="fc2a3-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="fc2a3-106">[in]緩衝區的長度，`pcConstants`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="fc2a3-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="fc2a3-107">[out]指標`ULONG32`接收大小，以字元為單位，以包含常數所需要的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fc2a3-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="fc2a3-108">[out]儲存常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="fc2a3-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc2a3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc2a3-109">Return Value</span></span>  
 <span data-ttu-id="fc2a3-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="fc2a3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc2a3-111">需求</span><span class="sxs-lookup"><span data-stu-id="fc2a3-111">Requirements</span></span>  
 <span data-ttu-id="fc2a3-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc2a3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2a3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc2a3-113">See also</span></span>

- [<span data-ttu-id="fc2a3-114">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="fc2a3-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

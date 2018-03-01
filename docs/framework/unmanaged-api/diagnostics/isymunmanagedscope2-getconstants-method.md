---
title: "ISymUnmanagedScope2::GetConstants 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: da0d2d39fcc1de8435c7af49a912764c79eb6583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="edd90-102">ISymUnmanagedScope2::GetConstants 方法</span><span class="sxs-lookup"><span data-stu-id="edd90-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="edd90-103">取得定義在這個範圍內的區域常數。</span><span class="sxs-lookup"><span data-stu-id="edd90-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edd90-104">語法</span><span class="sxs-lookup"><span data-stu-id="edd90-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edd90-105">參數</span><span class="sxs-lookup"><span data-stu-id="edd90-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="edd90-106">[in]緩衝區的長度，`pcConstants`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="edd90-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="edd90-107">[out]指標`ULONG32`接收以字元為單位，才能包含常數緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="edd90-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="edd90-108">[out]儲存常數緩衝區。</span><span class="sxs-lookup"><span data-stu-id="edd90-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edd90-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="edd90-109">Return Value</span></span>  
 <span data-ttu-id="edd90-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="edd90-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edd90-111">需求</span><span class="sxs-lookup"><span data-stu-id="edd90-111">Requirements</span></span>  
 <span data-ttu-id="edd90-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="edd90-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd90-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="edd90-113">See Also</span></span>  
 [<span data-ttu-id="edd90-114">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="edd90-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

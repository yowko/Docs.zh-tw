---
title: "ISymUnmanagedVariable::GetEndOffset 方法"
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
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f91c2b0f4ecb4cc901a0389d15f4d69e926cf8f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="a4def-102">ISymUnmanagedVariable::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a4def-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="a4def-103">取得其父系內這個變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="a4def-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="a4def-104">如果這是在範圍內的區域變數，結束位移會落在範圍定義的位移。</span><span class="sxs-lookup"><span data-stu-id="a4def-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4def-105">語法</span><span class="sxs-lookup"><span data-stu-id="a4def-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4def-106">參數</span><span class="sxs-lookup"><span data-stu-id="a4def-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a4def-107">[out]指標`ULONG32`接收的結束位移。</span><span class="sxs-lookup"><span data-stu-id="a4def-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4def-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4def-108">Return Value</span></span>  
 <span data-ttu-id="a4def-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a4def-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4def-110">需求</span><span class="sxs-lookup"><span data-stu-id="a4def-110">Requirements</span></span>  
 <span data-ttu-id="a4def-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a4def-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4def-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="a4def-112">See Also</span></span>  
 [<span data-ttu-id="a4def-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="a4def-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="a4def-114">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a4def-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)

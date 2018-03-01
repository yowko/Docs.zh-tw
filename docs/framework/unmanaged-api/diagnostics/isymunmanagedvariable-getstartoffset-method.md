---
title: "ISymUnmanagedVariable::GetStartOffset 方法"
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
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3fa0c710eb5de8b9a92970002336de22adb2458
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="172bf-102">ISymUnmanagedVariable::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="172bf-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="172bf-103">取得其父系內這個變數的起始位移。</span><span class="sxs-lookup"><span data-stu-id="172bf-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="172bf-104">如果這是在範圍內的區域變數的起始位移會落在範圍定義的位移。</span><span class="sxs-lookup"><span data-stu-id="172bf-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="172bf-105">語法</span><span class="sxs-lookup"><span data-stu-id="172bf-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="172bf-106">參數</span><span class="sxs-lookup"><span data-stu-id="172bf-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="172bf-107">[out]指標`ULONG32`接收的起始位移。</span><span class="sxs-lookup"><span data-stu-id="172bf-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="172bf-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="172bf-108">Return Value</span></span>  
 <span data-ttu-id="172bf-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="172bf-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="172bf-110">需求</span><span class="sxs-lookup"><span data-stu-id="172bf-110">Requirements</span></span>  
 <span data-ttu-id="172bf-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="172bf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="172bf-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="172bf-112">See Also</span></span>  
 [<span data-ttu-id="172bf-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="172bf-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="172bf-114">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="172bf-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)

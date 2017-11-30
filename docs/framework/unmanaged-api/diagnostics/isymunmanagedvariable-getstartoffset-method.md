---
title: "ISymUnmanagedVariable::GetStartOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b7fd3a64202224ef5a7cc348ee8e9974a664d09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="7af70-102">ISymUnmanagedVariable::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="7af70-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="7af70-103">取得其父系內這個變數的起始位移。</span><span class="sxs-lookup"><span data-stu-id="7af70-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="7af70-104">如果這是在範圍內的區域變數的起始位移會落在範圍定義的位移。</span><span class="sxs-lookup"><span data-stu-id="7af70-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af70-105">語法</span><span class="sxs-lookup"><span data-stu-id="7af70-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7af70-106">參數</span><span class="sxs-lookup"><span data-stu-id="7af70-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7af70-107">[out]指標`ULONG32`接收的起始位移。</span><span class="sxs-lookup"><span data-stu-id="7af70-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7af70-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7af70-108">Return Value</span></span>  
 <span data-ttu-id="7af70-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7af70-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7af70-110">需求</span><span class="sxs-lookup"><span data-stu-id="7af70-110">Requirements</span></span>  
 <span data-ttu-id="7af70-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7af70-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af70-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7af70-112">See Also</span></span>  
 [<span data-ttu-id="7af70-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="7af70-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="7af70-114">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="7af70-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)

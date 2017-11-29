---
title: "ISymUnmanagedVariable::GetEndOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7a2dac8425cd852c6c17ee1674710f6798d3b1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="7cb38-102">ISymUnmanagedVariable::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="7cb38-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="7cb38-103">取得其父系內這個變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="7cb38-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="7cb38-104">如果這是在範圍內的區域變數，結束位移會落在範圍定義的位移。</span><span class="sxs-lookup"><span data-stu-id="7cb38-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb38-105">語法</span><span class="sxs-lookup"><span data-stu-id="7cb38-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cb38-106">參數</span><span class="sxs-lookup"><span data-stu-id="7cb38-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7cb38-107">[out]指標`ULONG32`接收的結束位移。</span><span class="sxs-lookup"><span data-stu-id="7cb38-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cb38-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7cb38-108">Return Value</span></span>  
 <span data-ttu-id="7cb38-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cb38-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb38-110">需求</span><span class="sxs-lookup"><span data-stu-id="7cb38-110">Requirements</span></span>  
 <span data-ttu-id="7cb38-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7cb38-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb38-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cb38-112">See Also</span></span>  
 [<span data-ttu-id="7cb38-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="7cb38-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="7cb38-114">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="7cb38-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)

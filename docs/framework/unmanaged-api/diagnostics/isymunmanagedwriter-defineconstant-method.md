---
title: "ISymUnmanagedWriter::DefineConstant 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineConstant
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 910f2e753849b955a398f2175342b2f94849fba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="aca37-102">ISymUnmanagedWriter::DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="aca37-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="aca37-103">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="aca37-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca37-104">語法</span><span class="sxs-lookup"><span data-stu-id="aca37-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aca37-105">參數</span><span class="sxs-lookup"><span data-stu-id="aca37-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="aca37-106">[in]指標`WCHAR`定義常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="aca37-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="aca37-107">[in]常數的值。</span><span class="sxs-lookup"><span data-stu-id="aca37-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="aca37-108">[in] `signature` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="aca37-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="aca37-109">[in]常數類型簽章。</span><span class="sxs-lookup"><span data-stu-id="aca37-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aca37-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="aca37-110">Return Value</span></span>  
 <span data-ttu-id="aca37-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="aca37-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca37-112">需求</span><span class="sxs-lookup"><span data-stu-id="aca37-112">Requirements</span></span>  
 <span data-ttu-id="aca37-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aca37-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca37-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aca37-114">See Also</span></span>  
 [<span data-ttu-id="aca37-115">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="aca37-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="aca37-116">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="aca37-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)

---
title: "ISymUnmanagedWriter::DefineGlobalVariable 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineGlobalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7540dfcefbe7a331a26220a07b2e206c1302ddc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="1bc5b-102">ISymUnmanagedWriter::DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="1bc5b-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="1bc5b-103">定義單一的全域變數。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bc5b-104">Syntax</span></span>  
  
```  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bc5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bc5b-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="1bc5b-106">[in]指標`WCHAR`，定義全域變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="1bc5b-107">[in]全域變數的屬性。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="1bc5b-108">[in]A`ULONG32`指出的大小，以字元為單位的`signature`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="1bc5b-109">[in]全域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="1bc5b-110">[in]地址類型。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="1bc5b-111">[in]參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="1bc5b-112">[in]參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="1bc5b-113">[in]參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bc5b-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="1bc5b-114">Return Value</span></span>  
 <span data-ttu-id="1bc5b-115">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1bc5b-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bc5b-116">需求</span><span class="sxs-lookup"><span data-stu-id="1bc5b-116">Requirements</span></span>  
 <span data-ttu-id="1bc5b-117">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1bc5b-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc5b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc5b-118">See Also</span></span>  
 [<span data-ttu-id="1bc5b-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="1bc5b-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="1bc5b-120">DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="1bc5b-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)  
 [<span data-ttu-id="1bc5b-121">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="1bc5b-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)

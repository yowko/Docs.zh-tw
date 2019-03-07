---
title: ISymUnmanagedWriter::DefineGlobalVariable 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bba8d887bc516149135aae61c4f9bdb9a9e0c9d9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470532"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="af2f4-102">ISymUnmanagedWriter::DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="af2f4-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="af2f4-103">定義單一全域變數。</span><span class="sxs-lookup"><span data-stu-id="af2f4-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="af2f4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="af2f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="af2f4-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="af2f4-106">[in]指標`WCHAR`，定義全域變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="af2f4-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="af2f4-107">[in]全域變數的屬性。</span><span class="sxs-lookup"><span data-stu-id="af2f4-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="af2f4-108">[in]A`ULONG32`表示的大小，以字元為單位，`signature`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="af2f4-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="af2f4-109">[in]全域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="af2f4-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="af2f4-110">[in]位址類型。</span><span class="sxs-lookup"><span data-stu-id="af2f4-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="af2f4-111">[in]參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="af2f4-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="af2f4-112">[in]參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="af2f4-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="af2f4-113">[in]參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="af2f4-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af2f4-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="af2f4-114">Return Value</span></span>  
 <span data-ttu-id="af2f4-115">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="af2f4-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af2f4-116">需求</span><span class="sxs-lookup"><span data-stu-id="af2f4-116">Requirements</span></span>  
 <span data-ttu-id="af2f4-117">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="af2f4-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af2f4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af2f4-118">See also</span></span>
- [<span data-ttu-id="af2f4-119">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="af2f4-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="af2f4-120">DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="af2f4-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="af2f4-121">DefineGlobalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="af2f4-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)

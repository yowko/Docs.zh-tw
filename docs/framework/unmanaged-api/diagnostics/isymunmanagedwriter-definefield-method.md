---
title: "ISymUnmanagedWriter::DefineField 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineField
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c44c4ba4a2fd8959299bce6c9f3b4dc361174922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="e71f7-102">ISymUnmanagedWriter::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="e71f7-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="e71f7-103">定義單一變數不是在方法中。</span><span class="sxs-lookup"><span data-stu-id="e71f7-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="e71f7-104">這個方法是使用特定類別中的欄位、 位元欄位等等。</span><span class="sxs-lookup"><span data-stu-id="e71f7-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71f7-105">語法</span><span class="sxs-lookup"><span data-stu-id="e71f7-105">Syntax</span></span>  
  
```  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e71f7-106">參數</span><span class="sxs-lookup"><span data-stu-id="e71f7-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="e71f7-107">[in]在中繼資料類型或方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e71f7-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="e71f7-108">[in]欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="e71f7-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="e71f7-109">[in]欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="e71f7-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="e71f7-110">[in]A`ULONG32`也就是大小，以字元為單位，以包含欄位簽章所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e71f7-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="e71f7-111">[in]欄位簽章的陣列。</span><span class="sxs-lookup"><span data-stu-id="e71f7-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="e71f7-112">[in]地址類型。</span><span class="sxs-lookup"><span data-stu-id="e71f7-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="e71f7-113">[in]欄位規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="e71f7-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="e71f7-114">[in]欄位規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="e71f7-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="e71f7-115">[in]欄位規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="e71f7-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e71f7-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="e71f7-116">Return Value</span></span>  
 <span data-ttu-id="e71f7-117">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e71f7-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e71f7-118">需求</span><span class="sxs-lookup"><span data-stu-id="e71f7-118">Requirements</span></span>  
 <span data-ttu-id="e71f7-119">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e71f7-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71f7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e71f7-120">See Also</span></span>  
 [<span data-ttu-id="e71f7-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="e71f7-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

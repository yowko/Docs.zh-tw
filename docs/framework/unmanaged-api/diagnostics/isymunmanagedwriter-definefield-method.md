---
title: ISymUnmanagedWriter::DefineField 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03c0a9d7315f5158948701d4322887104f0844c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603660"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="a521a-102">ISymUnmanagedWriter::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="a521a-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="a521a-103">定義不在方法內的單一變數。</span><span class="sxs-lookup"><span data-stu-id="a521a-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="a521a-104">這個方法是使用特定類別中的欄位、 位元欄位，依此類推。</span><span class="sxs-lookup"><span data-stu-id="a521a-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a521a-105">語法</span><span class="sxs-lookup"><span data-stu-id="a521a-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="a521a-106">參數</span><span class="sxs-lookup"><span data-stu-id="a521a-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="a521a-107">[in]中繼資料型別或方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a521a-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="a521a-108">[in]欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="a521a-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="a521a-109">[in]欄位的欄位屬性。</span><span class="sxs-lookup"><span data-stu-id="a521a-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="a521a-110">[in]A`ULONG32`也就是大小，以字元為單位，以包含欄位簽章所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a521a-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="a521a-111">[in]欄位簽章的陣列。</span><span class="sxs-lookup"><span data-stu-id="a521a-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="a521a-112">[in]位址類型。</span><span class="sxs-lookup"><span data-stu-id="a521a-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="a521a-113">[in]欄位規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="a521a-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="a521a-114">[in]欄位規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="a521a-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="a521a-115">[in]欄位規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="a521a-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a521a-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="a521a-116">Return Value</span></span>  
 <span data-ttu-id="a521a-117">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a521a-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a521a-118">需求</span><span class="sxs-lookup"><span data-stu-id="a521a-118">Requirements</span></span>  
 <span data-ttu-id="a521a-119">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a521a-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a521a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a521a-120">See also</span></span>
- [<span data-ttu-id="a521a-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a521a-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

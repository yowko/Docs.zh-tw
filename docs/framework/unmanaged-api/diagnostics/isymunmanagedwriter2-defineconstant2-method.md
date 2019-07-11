---
title: ISymUnmanagedWriter2::DefineConstant2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c194cea21901015153626dc5aead49ed1b2c3df7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755106"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="b0ae6-102">ISymUnmanagedWriter2::DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="b0ae6-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="b0ae6-103">定義常值的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0ae6-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ae6-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0ae6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0ae6-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0ae6-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b0ae6-106">[in]常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0ae6-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="b0ae6-107">[in]常數的值。</span><span class="sxs-lookup"><span data-stu-id="b0ae6-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="b0ae6-108">[in]常數的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b0ae6-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0ae6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b0ae6-109">Return Value</span></span>  
 <span data-ttu-id="b0ae6-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0ae6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ae6-111">需求</span><span class="sxs-lookup"><span data-stu-id="b0ae6-111">Requirements</span></span>  
 <span data-ttu-id="b0ae6-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b0ae6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ae6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0ae6-113">See also</span></span>

- [<span data-ttu-id="b0ae6-114">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="b0ae6-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="b0ae6-115">DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="b0ae6-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)

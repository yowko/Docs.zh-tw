---
title: ISymUnmanagedWriter::SetSymAttribute 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1a55d4100d74b769b2bc1b8fe33d2042f5e739
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428297"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="74488-102">ISymUnmanagedWriter::SetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="74488-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="74488-103">定義自訂屬性，根據它的名稱。</span><span class="sxs-lookup"><span data-stu-id="74488-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="74488-104">這些屬性是存放在符號存放區中，不同於中繼資料的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="74488-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74488-105">語法</span><span class="sxs-lookup"><span data-stu-id="74488-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74488-106">參數</span><span class="sxs-lookup"><span data-stu-id="74488-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="74488-107">[in]中繼資料語彙基元，為其定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="74488-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="74488-108">[in]指標`WCHAR`，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="74488-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="74488-109">[in]A`ULONG32`指出的大小`data`陣列。</span><span class="sxs-lookup"><span data-stu-id="74488-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="74488-110">[in]屬性值。</span><span class="sxs-lookup"><span data-stu-id="74488-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74488-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="74488-111">Return Value</span></span>  
 <span data-ttu-id="74488-112">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="74488-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74488-113">需求</span><span class="sxs-lookup"><span data-stu-id="74488-113">Requirements</span></span>  
 <span data-ttu-id="74488-114">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="74488-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74488-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74488-115">See Also</span></span>  
 [<span data-ttu-id="74488-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="74488-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

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
ms.openlocfilehash: 8ffcc3a079e7e9a9d69622dc6666bb0e7641d4e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650767"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="84a0f-102">ISymUnmanagedWriter::SetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="84a0f-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="84a0f-103">定義自訂屬性，根據其名稱。</span><span class="sxs-lookup"><span data-stu-id="84a0f-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="84a0f-104">這些屬性會保存在符號存放區，不同於中繼資料的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="84a0f-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84a0f-105">語法</span><span class="sxs-lookup"><span data-stu-id="84a0f-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84a0f-106">參數</span><span class="sxs-lookup"><span data-stu-id="84a0f-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="84a0f-107">[in]中繼資料語彙基元，為其定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="84a0f-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="84a0f-108">[in]指標`WCHAR`，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="84a0f-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="84a0f-109">[in]A`ULONG32`表示的大小`data`陣列。</span><span class="sxs-lookup"><span data-stu-id="84a0f-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="84a0f-110">[in]屬性值。</span><span class="sxs-lookup"><span data-stu-id="84a0f-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84a0f-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="84a0f-111">Return Value</span></span>  
 <span data-ttu-id="84a0f-112">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="84a0f-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84a0f-113">需求</span><span class="sxs-lookup"><span data-stu-id="84a0f-113">Requirements</span></span>  
 <span data-ttu-id="84a0f-114">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="84a0f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a0f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84a0f-115">See also</span></span>

- [<span data-ttu-id="84a0f-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="84a0f-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

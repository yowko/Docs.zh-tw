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
ms.openlocfilehash: 4450c262b75a73114cb7de7de98567f053bbf564
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894473"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="53ddd-102">ISymUnmanagedWriter::SetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="53ddd-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="53ddd-103">根據名稱定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="53ddd-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="53ddd-104">這些屬性會保留在符號存放區中，不同于中繼資料自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="53ddd-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ddd-105">語法</span><span class="sxs-lookup"><span data-stu-id="53ddd-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53ddd-106">參數</span><span class="sxs-lookup"><span data-stu-id="53ddd-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="53ddd-107">在要定義屬性的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="53ddd-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="53ddd-108">在的指標`WCHAR` ，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="53ddd-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="53ddd-109">在，指出`data`陣列的大小。 `ULONG32`</span><span class="sxs-lookup"><span data-stu-id="53ddd-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="53ddd-110">在屬性值。</span><span class="sxs-lookup"><span data-stu-id="53ddd-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53ddd-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="53ddd-111">Return Value</span></span>  
 <span data-ttu-id="53ddd-112">如果方法成功，則為 S_OK;否則，E_FAIL 或其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="53ddd-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ddd-113">需求</span><span class="sxs-lookup"><span data-stu-id="53ddd-113">Requirements</span></span>  
 <span data-ttu-id="53ddd-114">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="53ddd-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ddd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ddd-115">See also</span></span>

- [<span data-ttu-id="53ddd-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="53ddd-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

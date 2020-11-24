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
ms.openlocfilehash: 484affb2ca87ca50a805d1bb46b7749d294d09f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683507"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="7af0c-102">ISymUnmanagedWriter::SetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="7af0c-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>

<span data-ttu-id="7af0c-103">根據名稱定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="7af0c-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="7af0c-104">這些屬性會保存在符號存放區中，與中繼資料自訂屬性不同。</span><span class="sxs-lookup"><span data-stu-id="7af0c-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af0c-105">語法</span><span class="sxs-lookup"><span data-stu-id="7af0c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7af0c-106">參數</span><span class="sxs-lookup"><span data-stu-id="7af0c-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="7af0c-107">在要定義屬性的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="7af0c-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="7af0c-108">在的指標 `WCHAR` ，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7af0c-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="7af0c-109">在 `ULONG32` ，指出陣列的大小 `data` 。</span><span class="sxs-lookup"><span data-stu-id="7af0c-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="7af0c-110">在屬性值。</span><span class="sxs-lookup"><span data-stu-id="7af0c-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7af0c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="7af0c-111">Return Value</span></span>  

 <span data-ttu-id="7af0c-112">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7af0c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7af0c-113">需求</span><span class="sxs-lookup"><span data-stu-id="7af0c-113">Requirements</span></span>  

 <span data-ttu-id="7af0c-114">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="7af0c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af0c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7af0c-115">See also</span></span>

- [<span data-ttu-id="7af0c-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="7af0c-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)

---
title: "ISymUnmanagedWriter::SetSymAttribute 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c59c3c8ec4534f0a7587d4fdb772683715363066
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="a194a-102">ISymUnmanagedWriter::SetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="a194a-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="a194a-103">定義自訂屬性，根據它的名稱。</span><span class="sxs-lookup"><span data-stu-id="a194a-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="a194a-104">這些屬性是存放在符號存放區中，不同於中繼資料的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="a194a-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a194a-105">語法</span><span class="sxs-lookup"><span data-stu-id="a194a-105">Syntax</span></span>  
  
```  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a194a-106">參數</span><span class="sxs-lookup"><span data-stu-id="a194a-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="a194a-107">[in]中繼資料語彙基元，為其定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="a194a-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="a194a-108">[in]指標`WCHAR`，其中包含屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="a194a-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="a194a-109">[in]A`ULONG32`指出的大小`data`陣列。</span><span class="sxs-lookup"><span data-stu-id="a194a-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="a194a-110">[in]屬性值。</span><span class="sxs-lookup"><span data-stu-id="a194a-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a194a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a194a-111">Return Value</span></span>  
 <span data-ttu-id="a194a-112">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a194a-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a194a-113">需求</span><span class="sxs-lookup"><span data-stu-id="a194a-113">Requirements</span></span>  
 <span data-ttu-id="a194a-114">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a194a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a194a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a194a-115">See Also</span></span>  
 [<span data-ttu-id="a194a-116">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a194a-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

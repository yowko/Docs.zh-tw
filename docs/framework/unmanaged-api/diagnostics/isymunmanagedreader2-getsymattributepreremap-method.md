---
title: "ISymUnmanagedReader2::GetSymAttributePreRemap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4a9e2304e746578fbe0e7a5c4d1b0ef1f1c8a1b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="f3c10-102">ISymUnmanagedReader2::GetSymAttributePreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="f3c10-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="f3c10-103">取得其名稱為基礎的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="f3c10-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="f3c10-104">不同於中繼資料的自訂屬性，這些屬性是存放在符號存放區中。</span><span class="sxs-lookup"><span data-stu-id="f3c10-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3c10-105">語法</span><span class="sxs-lookup"><span data-stu-id="f3c10-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3c10-106">參數</span><span class="sxs-lookup"><span data-stu-id="f3c10-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="f3c10-107">[in]父系中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f3c10-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="f3c10-108">[in]指標`WCHAR`其中包含的名稱。</span><span class="sxs-lookup"><span data-stu-id="f3c10-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="f3c10-109">[in]A`ULONG32`指出的大小`buffer`陣列。</span><span class="sxs-lookup"><span data-stu-id="f3c10-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="f3c10-110">[out]指標`ULONG32`包含屬性位元組所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="f3c10-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="f3c10-111">[out]接收屬性位元組的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="f3c10-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3c10-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f3c10-112">Return Value</span></span>  
 <span data-ttu-id="f3c10-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f3c10-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3c10-114">需求</span><span class="sxs-lookup"><span data-stu-id="f3c10-114">Requirements</span></span>  
 <span data-ttu-id="f3c10-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f3c10-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c10-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3c10-116">See Also</span></span>  
 [<span data-ttu-id="f3c10-117">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="f3c10-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

---
title: ISymUnmanagedReader2::GetSymAttributePreRemap 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 258d6967d1586974a4258e7906fd71db6c461b07
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482180"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="44867-102">ISymUnmanagedReader2::GetSymAttributePreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="44867-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="44867-103">取得自訂屬性，根據其名稱。</span><span class="sxs-lookup"><span data-stu-id="44867-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="44867-104">不同於中繼資料的自訂屬性，這些屬性會保存在符號存放區。</span><span class="sxs-lookup"><span data-stu-id="44867-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44867-105">語法</span><span class="sxs-lookup"><span data-stu-id="44867-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44867-106">參數</span><span class="sxs-lookup"><span data-stu-id="44867-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="44867-107">[in]父代的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="44867-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="44867-108">[in]指標`WCHAR`包含名稱。</span><span class="sxs-lookup"><span data-stu-id="44867-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="44867-109">[in]A`ULONG32`表示的大小`buffer`陣列。</span><span class="sxs-lookup"><span data-stu-id="44867-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="44867-110">[out]指標`ULONG32`接收包含屬性的位元組所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="44867-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="44867-111">[out]接收屬性位元組緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="44867-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44867-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="44867-112">Return Value</span></span>  
 <span data-ttu-id="44867-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="44867-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44867-114">需求</span><span class="sxs-lookup"><span data-stu-id="44867-114">Requirements</span></span>  
 <span data-ttu-id="44867-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="44867-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44867-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44867-116">See also</span></span>
- [<span data-ttu-id="44867-117">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="44867-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

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
ms.openlocfilehash: 326f970f53293b74bbf8c5e77830f3f6ce1b73ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427033"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="31aab-102">ISymUnmanagedReader2::GetSymAttributePreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="31aab-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="31aab-103">取得其名稱為基礎的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="31aab-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="31aab-104">不同於中繼資料的自訂屬性，這些屬性是存放在符號存放區中。</span><span class="sxs-lookup"><span data-stu-id="31aab-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31aab-105">語法</span><span class="sxs-lookup"><span data-stu-id="31aab-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31aab-106">參數</span><span class="sxs-lookup"><span data-stu-id="31aab-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="31aab-107">[in]父系中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="31aab-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="31aab-108">[in]指標`WCHAR`其中包含的名稱。</span><span class="sxs-lookup"><span data-stu-id="31aab-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="31aab-109">[in]A`ULONG32`指出的大小`buffer`陣列。</span><span class="sxs-lookup"><span data-stu-id="31aab-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="31aab-110">[out]指標`ULONG32`包含屬性位元組所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="31aab-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="31aab-111">[out]接收屬性位元組的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="31aab-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31aab-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="31aab-112">Return Value</span></span>  
 <span data-ttu-id="31aab-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="31aab-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31aab-114">需求</span><span class="sxs-lookup"><span data-stu-id="31aab-114">Requirements</span></span>  
 <span data-ttu-id="31aab-115">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31aab-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31aab-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31aab-116">See Also</span></span>  
 [<span data-ttu-id="31aab-117">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="31aab-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

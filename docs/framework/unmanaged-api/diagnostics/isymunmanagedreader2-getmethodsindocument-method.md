---
title: ISymUnmanagedReader2::GetMethodsInDocument 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28b240159c36b03b2c476f56f7e6ad7b33f20649
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142337"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="4661c-102">ISymUnmanagedReader2::GetMethodsInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="4661c-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="4661c-103">取得每個提供的文件中具有行資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="4661c-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4661c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4661c-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4661c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4661c-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="4661c-106">[in]文件指標。</span><span class="sxs-lookup"><span data-stu-id="4661c-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="4661c-107">[in]A`ULONG32`表示的大小`pRetVal`陣列。</span><span class="sxs-lookup"><span data-stu-id="4661c-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="4661c-108">[out]指標`ULONG32`接收包含方法所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="4661c-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4661c-109">[out]方法會接收緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="4661c-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4661c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4661c-110">Return Value</span></span>  
 <span data-ttu-id="4661c-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="4661c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4661c-112">需求</span><span class="sxs-lookup"><span data-stu-id="4661c-112">Requirements</span></span>  
 <span data-ttu-id="4661c-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4661c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4661c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4661c-114">See also</span></span>

- [<span data-ttu-id="4661c-115">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="4661c-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

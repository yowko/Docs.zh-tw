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
ms.openlocfilehash: 68a0f9ec8793d465a6fa3b1cb6936eddd7be4c8f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615406"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="d9367-102">ISymUnmanagedReader2::GetMethodsInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="d9367-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="d9367-103">取得提供的檔中具有行資訊的每一個方法。</span><span class="sxs-lookup"><span data-stu-id="d9367-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9367-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9367-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9367-105">參數</span><span class="sxs-lookup"><span data-stu-id="d9367-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d9367-106">在檔的指標。</span><span class="sxs-lookup"><span data-stu-id="d9367-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="d9367-107">在`ULONG32`，指出陣列的大小 `pRetVal` 。</span><span class="sxs-lookup"><span data-stu-id="d9367-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="d9367-108">脫銷的指標 `ULONG32` ，接收包含方法所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="d9367-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d9367-109">脫銷接收方法之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="d9367-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9367-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9367-110">Return Value</span></span>  
 <span data-ttu-id="d9367-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d9367-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9367-112">需求</span><span class="sxs-lookup"><span data-stu-id="d9367-112">Requirements</span></span>  
 <span data-ttu-id="d9367-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d9367-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9367-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9367-114">See also</span></span>

- [<span data-ttu-id="d9367-115">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="d9367-115">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)

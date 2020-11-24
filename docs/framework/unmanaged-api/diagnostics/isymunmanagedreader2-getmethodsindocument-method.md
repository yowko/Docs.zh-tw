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
ms.openlocfilehash: 2e7eb183200c6e6de8ee18b58aab457c7e7bf2eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675746"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="e07aa-102">ISymUnmanagedReader2::GetMethodsInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="e07aa-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>

<span data-ttu-id="e07aa-103">取得在提供的檔中有行資訊的每個方法。</span><span class="sxs-lookup"><span data-stu-id="e07aa-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="e07aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e07aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="e07aa-105">Parameters</span></span>  

 `document`  
 <span data-ttu-id="e07aa-106">在檔的指標。</span><span class="sxs-lookup"><span data-stu-id="e07aa-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="e07aa-107">在 `ULONG32` ，指出陣列的大小  `pRetVal` 。</span><span class="sxs-lookup"><span data-stu-id="e07aa-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="e07aa-108">擴展的指標 `ULONG32` ，會接收包含方法所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e07aa-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e07aa-109">擴展接收方法之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="e07aa-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e07aa-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e07aa-110">Return Value</span></span>  

 <span data-ttu-id="e07aa-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e07aa-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07aa-112">需求</span><span class="sxs-lookup"><span data-stu-id="e07aa-112">Requirements</span></span>  

 <span data-ttu-id="e07aa-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e07aa-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07aa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e07aa-114">See also</span></span>

- [<span data-ttu-id="e07aa-115">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="e07aa-115">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)

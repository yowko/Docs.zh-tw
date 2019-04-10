---
title: ISymUnmanagedMethod::GetOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a42dc624d4de9cddebad287f6d90590f96b30272
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223650"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="c8ef2-102">ISymUnmanagedMethod::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="c8ef2-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="c8ef2-103">文件中的指定位置傳回此對應的方法中的位移。</span><span class="sxs-lookup"><span data-stu-id="c8ef2-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ef2-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8ef2-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8ef2-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8ef2-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="c8ef2-106">[in]要求位移的文件指標。</span><span class="sxs-lookup"><span data-stu-id="c8ef2-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="c8ef2-107">[in]要求位移的文件行。</span><span class="sxs-lookup"><span data-stu-id="c8ef2-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="c8ef2-108">[in]要求位移的文件的資料行。</span><span class="sxs-lookup"><span data-stu-id="c8ef2-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c8ef2-109">[out]指標`ULONG32`接收位移。</span><span class="sxs-lookup"><span data-stu-id="c8ef2-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8ef2-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8ef2-110">Return Value</span></span>  
 <span data-ttu-id="c8ef2-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c8ef2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8ef2-112">需求</span><span class="sxs-lookup"><span data-stu-id="c8ef2-112">Requirements</span></span>  
 <span data-ttu-id="c8ef2-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c8ef2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ef2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8ef2-114">See also</span></span>

- [<span data-ttu-id="c8ef2-115">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c8ef2-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

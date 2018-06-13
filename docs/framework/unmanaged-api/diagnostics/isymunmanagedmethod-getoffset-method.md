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
ms.openlocfilehash: 6d88e9279f70c36fd8a9c626972e33305cded5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424387"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="56e36-102">ISymUnmanagedMethod::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="56e36-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="56e36-103">回到文件中的指定位置中對應這個方法內位移。</span><span class="sxs-lookup"><span data-stu-id="56e36-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e36-104">語法</span><span class="sxs-lookup"><span data-stu-id="56e36-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56e36-105">參數</span><span class="sxs-lookup"><span data-stu-id="56e36-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="56e36-106">[in]要求位移的文件指標。</span><span class="sxs-lookup"><span data-stu-id="56e36-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="56e36-107">[in]要求位移的文件行。</span><span class="sxs-lookup"><span data-stu-id="56e36-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="56e36-108">[in]要求位移的文件的資料行。</span><span class="sxs-lookup"><span data-stu-id="56e36-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="56e36-109">[out]指標`ULONG32`接收的位移。</span><span class="sxs-lookup"><span data-stu-id="56e36-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56e36-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="56e36-110">Return Value</span></span>  
 <span data-ttu-id="56e36-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="56e36-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56e36-112">需求</span><span class="sxs-lookup"><span data-stu-id="56e36-112">Requirements</span></span>  
 <span data-ttu-id="56e36-113">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56e36-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e36-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56e36-114">See Also</span></span>  
 [<span data-ttu-id="56e36-115">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="56e36-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

---
title: ISymUnmanagedReader::GetMethodByVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebf2fea9f987818c93a1e865f2ed2ce33142050c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468659"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="f2ba2-102">ISymUnmanagedReader::GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="f2ba2-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="f2ba2-103">取得符號讀取器方法，指定方法的語彙基元和編輯複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="f2ba2-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="f2ba2-104">版本號碼從 1 開始，就會遞增每次編輯複製作業造成變更的方法時。</span><span class="sxs-lookup"><span data-stu-id="f2ba2-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ba2-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2ba2-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2ba2-106">參數</span><span class="sxs-lookup"><span data-stu-id="f2ba2-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="f2ba2-107">[in]方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f2ba2-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="f2ba2-108">[in]方法的版本。</span><span class="sxs-lookup"><span data-stu-id="f2ba2-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f2ba2-109">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f2ba2-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2ba2-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2ba2-110">Return Value</span></span>  
 <span data-ttu-id="f2ba2-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2ba2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2ba2-112">需求</span><span class="sxs-lookup"><span data-stu-id="f2ba2-112">Requirements</span></span>  
 <span data-ttu-id="f2ba2-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f2ba2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ba2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2ba2-114">See also</span></span>
- [<span data-ttu-id="f2ba2-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="f2ba2-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

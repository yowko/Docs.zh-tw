---
title: ISymUnmanagedReader::GetMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: deb5d7aa24cf750a9584ef2aa32d10816ec12f57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614402"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="43b79-102">ISymUnmanagedReader::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="43b79-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="43b79-103">取得符號讀取器方法，指定方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="43b79-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b79-104">語法</span><span class="sxs-lookup"><span data-stu-id="43b79-104">Syntax</span></span>  
  
```  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43b79-105">參數</span><span class="sxs-lookup"><span data-stu-id="43b79-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="43b79-106">[in]方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="43b79-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="43b79-107">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="43b79-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43b79-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="43b79-108">Return Value</span></span>  
 <span data-ttu-id="43b79-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="43b79-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43b79-110">需求</span><span class="sxs-lookup"><span data-stu-id="43b79-110">Requirements</span></span>  
 <span data-ttu-id="43b79-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="43b79-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b79-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43b79-112">See also</span></span>
- [<span data-ttu-id="43b79-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="43b79-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

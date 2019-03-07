---
title: ISymUnmanagedReader::GetMethodVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 364742957d16f12508d2df6f4cd7f50d7956d4cb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479450"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="128ff-102">ISymUnmanagedReader::GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="128ff-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="128ff-103">取得方法的版本。</span><span class="sxs-lookup"><span data-stu-id="128ff-103">Gets the method version.</span></span> <span data-ttu-id="128ff-104">方法版本 1 開始，並會遞增每次重新編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="128ff-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="128ff-105">此方法可能會重新編譯發生而不需要變更。</span><span class="sxs-lookup"><span data-stu-id="128ff-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="128ff-106">語法</span><span class="sxs-lookup"><span data-stu-id="128ff-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="128ff-107">參數</span><span class="sxs-lookup"><span data-stu-id="128ff-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="128ff-108">[in]要取得版本方法。</span><span class="sxs-lookup"><span data-stu-id="128ff-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="128ff-109">[out]此變數會接收方法版本指標。</span><span class="sxs-lookup"><span data-stu-id="128ff-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="128ff-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="128ff-110">Return Value</span></span>  
 <span data-ttu-id="128ff-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="128ff-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="128ff-112">需求</span><span class="sxs-lookup"><span data-stu-id="128ff-112">Requirements</span></span>  
 <span data-ttu-id="128ff-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="128ff-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128ff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="128ff-114">See also</span></span>
- [<span data-ttu-id="128ff-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="128ff-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

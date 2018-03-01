---
title: "ISymUnmanagedWriter::RemapToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86d6c78a49c55bdc9093241952bee00ee331696e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="f8b1e-102">ISymUnmanagedWriter::RemapToken 方法</span><span class="sxs-lookup"><span data-stu-id="f8b1e-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="f8b1e-103">通知中繼資料語彙基元已重新對應，因為中繼資料已發出符號寫入器。</span><span class="sxs-lookup"><span data-stu-id="f8b1e-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="f8b1e-104">如果符號寫入器已存放在符號存放區中舊的語彙基元，則它必須的更新與新的值，或者預存的語彙基元必須儲存對應的符號讀取器讀取階段期間重新對應的對應。</span><span class="sxs-lookup"><span data-stu-id="f8b1e-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8b1e-105">語法</span><span class="sxs-lookup"><span data-stu-id="f8b1e-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8b1e-106">參數</span><span class="sxs-lookup"><span data-stu-id="f8b1e-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="f8b1e-107">[in]已重新對應中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f8b1e-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="f8b1e-108">[in]新的中繼資料語彙基元的`oldToken`重新對應。</span><span class="sxs-lookup"><span data-stu-id="f8b1e-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8b1e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f8b1e-109">Return Value</span></span>  
 <span data-ttu-id="f8b1e-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f8b1e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8b1e-111">需求</span><span class="sxs-lookup"><span data-stu-id="f8b1e-111">Requirements</span></span>  
 <span data-ttu-id="f8b1e-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8b1e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b1e-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8b1e-113">See Also</span></span>  
 [<span data-ttu-id="f8b1e-114">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="f8b1e-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)

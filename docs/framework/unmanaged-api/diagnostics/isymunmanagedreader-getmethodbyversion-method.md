---
title: "ISymUnmanagedReader::GetMethodByVersion 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodByVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 810cc5cda9de7c61c1b23d1574ceff19bfec3bc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="8a279-102">ISymUnmanagedReader::GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="8a279-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="8a279-103">取得符號讀取器方法，指定方法語彙基元和編輯複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="8a279-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="8a279-104">版本號碼從 1 開始，就會遞增每次方法變更時編輯複製作業的結果。</span><span class="sxs-lookup"><span data-stu-id="8a279-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a279-105">語法</span><span class="sxs-lookup"><span data-stu-id="8a279-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a279-106">參數</span><span class="sxs-lookup"><span data-stu-id="8a279-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="8a279-107">[in]方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8a279-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="8a279-108">[in]方法的版本。</span><span class="sxs-lookup"><span data-stu-id="8a279-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8a279-109">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="8a279-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a279-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a279-110">Return Value</span></span>  
 <span data-ttu-id="8a279-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8a279-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a279-112">需求</span><span class="sxs-lookup"><span data-stu-id="8a279-112">Requirements</span></span>  
 <span data-ttu-id="8a279-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8a279-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a279-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a279-114">See Also</span></span>  
 [<span data-ttu-id="8a279-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="8a279-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

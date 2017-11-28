---
title: "ISymUnmanagedReader2::GetMethodByVersionPreRemap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 69a203424320a176cd285c23d98111e71709042a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="e665c-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="e665c-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="e665c-103">取得符號讀取器方法，指定方法語彙基元和編輯後繼續版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e665c-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="e665c-104">版本號碼從 1 開始，就會遞增每次方法做為編輯後繼續作業結果變更時。</span><span class="sxs-lookup"><span data-stu-id="e665c-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e665c-105">語法</span><span class="sxs-lookup"><span data-stu-id="e665c-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e665c-106">參數</span><span class="sxs-lookup"><span data-stu-id="e665c-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="e665c-107">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e665c-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="e665c-108">[in]方法的版本。</span><span class="sxs-lookup"><span data-stu-id="e665c-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e665c-109">[out]所傳回的指標[ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e665c-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e665c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e665c-110">Return Value</span></span>  
 <span data-ttu-id="e665c-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e665c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e665c-112">需求</span><span class="sxs-lookup"><span data-stu-id="e665c-112">Requirements</span></span>  
 <span data-ttu-id="e665c-113">**標頭：**於 CorSym.idl。</span><span class="sxs-lookup"><span data-stu-id="e665c-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="e665c-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e665c-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e665c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e665c-115">See Also</span></span>  
 [<span data-ttu-id="e665c-116">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="e665c-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

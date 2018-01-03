---
title: "ISymUnmanagedReader::GetMethodVersion 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodVersion
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713b8a89c9519abe407ac1d68adb2552cd012b1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="005b7-102">ISymUnmanagedReader::GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="005b7-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="005b7-103">取得方法的版本。</span><span class="sxs-lookup"><span data-stu-id="005b7-103">Gets the method version.</span></span> <span data-ttu-id="005b7-104">方法版本 1 開始，且會增加的每當重新編譯的方法。</span><span class="sxs-lookup"><span data-stu-id="005b7-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="005b7-105">重新編譯的方法可能會發生不需要任何變更。</span><span class="sxs-lookup"><span data-stu-id="005b7-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="005b7-106">語法</span><span class="sxs-lookup"><span data-stu-id="005b7-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="005b7-107">參數</span><span class="sxs-lookup"><span data-stu-id="005b7-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="005b7-108">[in]要取得版本方法。</span><span class="sxs-lookup"><span data-stu-id="005b7-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="005b7-109">[out]變數會接收方法版本的指標。</span><span class="sxs-lookup"><span data-stu-id="005b7-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="005b7-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="005b7-110">Return Value</span></span>  
 <span data-ttu-id="005b7-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="005b7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="005b7-112">需求</span><span class="sxs-lookup"><span data-stu-id="005b7-112">Requirements</span></span>  
 <span data-ttu-id="005b7-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="005b7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005b7-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="005b7-114">See Also</span></span>  
 [<span data-ttu-id="005b7-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="005b7-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

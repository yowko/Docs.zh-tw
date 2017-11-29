---
title: "ISymENCUnmanagedMethod::GetFileNameFromOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9dcdbf7813c7ce3d451a27c0abf08c661a8f17b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="ed927-102">ISymENCUnmanagedMethod::GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="ed927-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="ed927-103">取得行位移與相關聯的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ed927-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed927-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed927-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed927-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed927-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="ed927-106">[in]A`ULONG32`包含位移。</span><span class="sxs-lookup"><span data-stu-id="ed927-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ed927-107">[in]A`ULONG32`指出的大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ed927-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ed927-108">[out]指標`ULONG32`接收以字元為單位，以包含檔案名稱所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="ed927-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="ed927-109">[out]包含檔案名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ed927-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed927-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ed927-110">Return Value</span></span>  
 <span data-ttu-id="ed927-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed927-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed927-112">需求</span><span class="sxs-lookup"><span data-stu-id="ed927-112">Requirements</span></span>  
 <span data-ttu-id="ed927-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ed927-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed927-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed927-114">See Also</span></span>  
 [<span data-ttu-id="ed927-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="ed927-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

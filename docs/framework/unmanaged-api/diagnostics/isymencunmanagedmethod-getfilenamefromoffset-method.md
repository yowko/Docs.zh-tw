---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 494f39855132bc4a9551b78f746517862d285034
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074725"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="25715-102">ISymENCUnmanagedMethod::GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="25715-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="25715-103">取得行位移與相關聯的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="25715-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25715-104">語法</span><span class="sxs-lookup"><span data-stu-id="25715-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25715-105">參數</span><span class="sxs-lookup"><span data-stu-id="25715-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="25715-106">[in]A`ULONG32`包含位移。</span><span class="sxs-lookup"><span data-stu-id="25715-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="25715-107">[in]A`ULONG32`表示的大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="25715-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="25715-108">[out]指標`ULONG32`接收大小，以字元為單位，以包含檔案名稱所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="25715-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="25715-109">[out]包含檔案名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="25715-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25715-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="25715-110">Return Value</span></span>  
 <span data-ttu-id="25715-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="25715-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25715-112">需求</span><span class="sxs-lookup"><span data-stu-id="25715-112">Requirements</span></span>  
 <span data-ttu-id="25715-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25715-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25715-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25715-114">See also</span></span>

- [<span data-ttu-id="25715-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="25715-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

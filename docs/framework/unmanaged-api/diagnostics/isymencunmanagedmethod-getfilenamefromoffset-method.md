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
ms.openlocfilehash: 80bfdc9d58a86bb4cf945f0c8106bcfc00f3743e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760308"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="edb62-102">ISymENCUnmanagedMethod::GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="edb62-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="edb62-103">取得行位移與相關聯的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="edb62-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edb62-104">語法</span><span class="sxs-lookup"><span data-stu-id="edb62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edb62-105">參數</span><span class="sxs-lookup"><span data-stu-id="edb62-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="edb62-106">[in]A`ULONG32`包含位移。</span><span class="sxs-lookup"><span data-stu-id="edb62-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="edb62-107">[in]A`ULONG32`表示的大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="edb62-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="edb62-108">[out]指標`ULONG32`接收大小，以字元為單位，以包含檔案名稱所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="edb62-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="edb62-109">[out]包含檔案名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="edb62-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edb62-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="edb62-110">Return Value</span></span>  
 <span data-ttu-id="edb62-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="edb62-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edb62-112">需求</span><span class="sxs-lookup"><span data-stu-id="edb62-112">Requirements</span></span>  
 <span data-ttu-id="edb62-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="edb62-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb62-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edb62-114">See also</span></span>

- [<span data-ttu-id="edb62-115">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="edb62-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

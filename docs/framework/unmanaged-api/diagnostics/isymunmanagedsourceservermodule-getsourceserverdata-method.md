---
title: ISymUnmanagedSourceServerModule::GetSourceServerData 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71251af116fc8d634b822e1daa49d90e91fec6f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648819"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="257bb-102">ISymUnmanagedSourceServerModule::GetSourceServerData 方法</span><span class="sxs-lookup"><span data-stu-id="257bb-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="257bb-103">傳回模組的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="257bb-103">Returns the source server data for the module.</span></span> <span data-ttu-id="257bb-104">呼叫端必須使用釋放資源`CoTaskMemFree`。</span><span class="sxs-lookup"><span data-stu-id="257bb-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="257bb-105">語法</span><span class="sxs-lookup"><span data-stu-id="257bb-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="257bb-106">參數</span><span class="sxs-lookup"><span data-stu-id="257bb-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="257bb-107">[out]指標`ULONG32`接收大小，以位元組為單位的來源伺服器資料。</span><span class="sxs-lookup"><span data-stu-id="257bb-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="257bb-108">[out]所傳回的指標`pDataByteCount`值。</span><span class="sxs-lookup"><span data-stu-id="257bb-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="257bb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="257bb-109">Return Value</span></span>  
 <span data-ttu-id="257bb-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="257bb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="257bb-111">需求</span><span class="sxs-lookup"><span data-stu-id="257bb-111">Requirements</span></span>  
 <span data-ttu-id="257bb-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="257bb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="257bb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="257bb-113">See also</span></span>
- [<span data-ttu-id="257bb-114">ISymUnmanagedSourceServerModule 介面</span><span class="sxs-lookup"><span data-stu-id="257bb-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

---
title: IMetaDataDispenserEx::GetCORSystemDirectory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: fb673666543bea3df44005ee3b20d311524f51d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175911"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="f33b5-102">IMetaDataDispenserEx::GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="f33b5-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="f33b5-103">獲取保存當前通用語言運行時 （CLR） 的目錄。</span><span class="sxs-lookup"><span data-stu-id="f33b5-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="f33b5-104">此方法僅支援進程外調試器使用。</span><span class="sxs-lookup"><span data-stu-id="f33b5-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="f33b5-105">如果從其他元件調用，它將返回E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="f33b5-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f33b5-106">語法</span><span class="sxs-lookup"><span data-stu-id="f33b5-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f33b5-107">參數</span><span class="sxs-lookup"><span data-stu-id="f33b5-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="f33b5-108">[出]要接收目錄名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f33b5-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f33b5-109">[在]的大小（以位元組為單位）的大小`szBuffer`。</span><span class="sxs-lookup"><span data-stu-id="f33b5-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="f33b5-110">[出]在 中`szBuffer`實際返回的位元組數。</span><span class="sxs-lookup"><span data-stu-id="f33b5-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f33b5-111">需求</span><span class="sxs-lookup"><span data-stu-id="f33b5-111">Requirements</span></span>  
 <span data-ttu-id="f33b5-112">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f33b5-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f33b5-113">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="f33b5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f33b5-114">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f33b5-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f33b5-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f33b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33b5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f33b5-116">See also</span></span>

- [<span data-ttu-id="f33b5-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="f33b5-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="f33b5-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="f33b5-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)

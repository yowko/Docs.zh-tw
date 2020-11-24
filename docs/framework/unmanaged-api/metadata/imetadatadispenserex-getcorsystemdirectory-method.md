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
ms.openlocfilehash: ea0e6f96028afc201f498119976eb87aa762a6eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681687"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="09eda-102">IMetaDataDispenserEx::GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="09eda-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>

<span data-ttu-id="09eda-103">取得保存目前 common language runtime (CLR) 的目錄。</span><span class="sxs-lookup"><span data-stu-id="09eda-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="09eda-104">只有跨進程偵錯工具才能使用此方法。</span><span class="sxs-lookup"><span data-stu-id="09eda-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="09eda-105">如果從另一個元件呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="09eda-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09eda-106">語法</span><span class="sxs-lookup"><span data-stu-id="09eda-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09eda-107">參數</span><span class="sxs-lookup"><span data-stu-id="09eda-107">Parameters</span></span>  

 `szBuffer`  
 <span data-ttu-id="09eda-108">擴展要接收目錄名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="09eda-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="09eda-109">在的大小（以位元組為單位） `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="09eda-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="09eda-110">擴展實際傳回的位元組數目 `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="09eda-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09eda-111">需求</span><span class="sxs-lookup"><span data-stu-id="09eda-111">Requirements</span></span>  

 <span data-ttu-id="09eda-112">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09eda-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09eda-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="09eda-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09eda-114">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="09eda-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09eda-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09eda-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09eda-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09eda-116">See also</span></span>

- [<span data-ttu-id="09eda-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="09eda-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="09eda-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="09eda-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)

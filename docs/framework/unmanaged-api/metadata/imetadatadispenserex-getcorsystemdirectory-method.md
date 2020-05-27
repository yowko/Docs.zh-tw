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
ms.openlocfilehash: a76c17e663fdf6555ed878cca1b86b6a9395730e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008790"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="14704-102">IMetaDataDispenserEx::GetCORSystemDirectory 方法</span><span class="sxs-lookup"><span data-stu-id="14704-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="14704-103">取得保存目前 common language runtime （CLR）的目錄。</span><span class="sxs-lookup"><span data-stu-id="14704-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="14704-104">這個方法僅支援跨進程偵錯工具使用。</span><span class="sxs-lookup"><span data-stu-id="14704-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="14704-105">如果從另一個元件呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="14704-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14704-106">語法</span><span class="sxs-lookup"><span data-stu-id="14704-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14704-107">參數</span><span class="sxs-lookup"><span data-stu-id="14704-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="14704-108">脫銷要接收目錄名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="14704-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="14704-109">在的大小（以位元組為單位） `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="14704-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="14704-110">脫銷中實際傳回的位元組數目 `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="14704-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14704-111">需求</span><span class="sxs-lookup"><span data-stu-id="14704-111">Requirements</span></span>  
 <span data-ttu-id="14704-112">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14704-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14704-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="14704-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14704-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="14704-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14704-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14704-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14704-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14704-116">See also</span></span>

- [<span data-ttu-id="14704-117">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="14704-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="14704-118">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="14704-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)

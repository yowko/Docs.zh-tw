---
title: CreateInstallReferenceEnum 函式
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
ms.openlocfilehash: 0f62b05ebbd8b27dba160c8281c1d40748c90fc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688831"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="420ec-102">CreateInstallReferenceEnum 函式</span><span class="sxs-lookup"><span data-stu-id="420ec-102">CreateInstallReferenceEnum Function</span></span>

<span data-ttu-id="420ec-103">取得 [IInstallReferenceEnum](iinstallreferenceenum-interface.md) 實例的指標，該實例表示應用程式對指定元件的參考清單。</span><span class="sxs-lookup"><span data-stu-id="420ec-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="420ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="420ec-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="420ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="420ec-105">Parameters</span></span>  

 `ppRefEnum`  
 <span data-ttu-id="420ec-106">擴展傳回的 `IInstallReferenceEnum` 指標。</span><span class="sxs-lookup"><span data-stu-id="420ec-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="420ec-107">在識別要列舉參考之元件的 [IAssemblyName](iassemblyname-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="420ec-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="420ec-108">在影響列舉值行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="420ec-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="420ec-109">在保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="420ec-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="420ec-110">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="420ec-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="420ec-111">需求</span><span class="sxs-lookup"><span data-stu-id="420ec-111">Requirements</span></span>  

 <span data-ttu-id="420ec-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="420ec-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="420ec-113">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="420ec-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="420ec-114">連結 **庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="420ec-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="420ec-115">使用 Fusion.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="420ec-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="420ec-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="420ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420ec-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="420ec-117">See also</span></span>

- [<span data-ttu-id="420ec-118">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="420ec-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="420ec-119">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="420ec-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="420ec-120">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="420ec-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

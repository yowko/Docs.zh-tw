---
title: IInstallReferenceEnum 介面
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
ms.openlocfilehash: f56a9049cd4b503124abe9dd4866dc91779e268e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721058"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="1333c-102">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1333c-102">IInstallReferenceEnum Interface</span></span>

<span data-ttu-id="1333c-103">代表安裝在全域組件快取中參考元件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1333c-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1333c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1333c-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1333c-105">方法</span><span class="sxs-lookup"><span data-stu-id="1333c-105">Methods</span></span>  
  
|<span data-ttu-id="1333c-106">方法</span><span class="sxs-lookup"><span data-stu-id="1333c-106">Method</span></span>|<span data-ttu-id="1333c-107">描述</span><span class="sxs-lookup"><span data-stu-id="1333c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1333c-108">GetNextInstallReferenceItem 方法</span><span class="sxs-lookup"><span data-stu-id="1333c-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="1333c-109">取得這個所包含下一個的指標 `IInstallReferenceItem` `IInstallReferenceEnum` 。</span><span class="sxs-lookup"><span data-stu-id="1333c-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1333c-110">需求</span><span class="sxs-lookup"><span data-stu-id="1333c-110">Requirements</span></span>  

 <span data-ttu-id="1333c-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1333c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1333c-112">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="1333c-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1333c-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1333c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1333c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1333c-114">See also</span></span>

- [<span data-ttu-id="1333c-115">融合介面</span><span class="sxs-lookup"><span data-stu-id="1333c-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="1333c-116">IInstallReferenceItem 介面</span><span class="sxs-lookup"><span data-stu-id="1333c-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)

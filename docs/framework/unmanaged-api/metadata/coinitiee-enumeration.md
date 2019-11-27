---
title: COINITIEE 列舉
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: 2ccc038b4420040779dae70f15e3a8827ba94180
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444111"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="05504-102">COINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="05504-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="05504-103">指定初始化 common language runtime 時， [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)所使用的常數。</span><span class="sxs-lookup"><span data-stu-id="05504-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05504-104">語法</span><span class="sxs-lookup"><span data-stu-id="05504-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="05504-105">Members</span><span class="sxs-lookup"><span data-stu-id="05504-105">Members</span></span>  
  
|<span data-ttu-id="05504-106">成員</span><span class="sxs-lookup"><span data-stu-id="05504-106">Member</span></span>|<span data-ttu-id="05504-107">描述</span><span class="sxs-lookup"><span data-stu-id="05504-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="05504-108">預設初始化模式。</span><span class="sxs-lookup"><span data-stu-id="05504-108">Default initialization mode.</span></span> <span data-ttu-id="05504-109">這會初始化執行時間並建立預設 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="05504-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="05504-110">初始化以執行 managed DLL。</span><span class="sxs-lookup"><span data-stu-id="05504-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="05504-111">初始化以執行受控 EXE。</span><span class="sxs-lookup"><span data-stu-id="05504-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="05504-112">這會初始化執行時間，但不會建立預設 <xref:System.AppDomain>，這會在輸入 EXE 的主要常式之後建立。</span><span class="sxs-lookup"><span data-stu-id="05504-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05504-113">需求</span><span class="sxs-lookup"><span data-stu-id="05504-113">Requirements</span></span>  
 <span data-ttu-id="05504-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05504-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05504-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="05504-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05504-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="05504-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05504-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05504-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05504-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05504-118">See also</span></span>

- [<span data-ttu-id="05504-119">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="05504-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

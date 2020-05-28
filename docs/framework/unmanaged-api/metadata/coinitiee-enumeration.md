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
ms.openlocfilehash: f4d1c2f105abb64bf196d0dd8371c2788c97336e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005904"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="f27e6-102">COINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="f27e6-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="f27e6-103">指定初始化 common language runtime 時， [CoInitializeEE](../hosting/coinitializeee-function.md)所使用的常數。</span><span class="sxs-lookup"><span data-stu-id="f27e6-103">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="f27e6-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="f27e6-105">成員</span><span class="sxs-lookup"><span data-stu-id="f27e6-105">Members</span></span>  
  
|<span data-ttu-id="f27e6-106">成員</span><span class="sxs-lookup"><span data-stu-id="f27e6-106">Member</span></span>|<span data-ttu-id="f27e6-107">描述</span><span class="sxs-lookup"><span data-stu-id="f27e6-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="f27e6-108">預設初始化模式。</span><span class="sxs-lookup"><span data-stu-id="f27e6-108">Default initialization mode.</span></span> <span data-ttu-id="f27e6-109">這會初始化執行時間並建立預設值 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="f27e6-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="f27e6-110">初始化以執行 managed DLL。</span><span class="sxs-lookup"><span data-stu-id="f27e6-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="f27e6-111">初始化以執行受控 EXE。</span><span class="sxs-lookup"><span data-stu-id="f27e6-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="f27e6-112">這會初始化執行時間，但不會建立預設值 <xref:System.AppDomain> ，這會在輸入 EXE 的主要常式之後建立。</span><span class="sxs-lookup"><span data-stu-id="f27e6-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f27e6-113">需求</span><span class="sxs-lookup"><span data-stu-id="f27e6-113">Requirements</span></span>  
 <span data-ttu-id="f27e6-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f27e6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f27e6-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f27e6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f27e6-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f27e6-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f27e6-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f27e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f27e6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f27e6-118">See also</span></span>

- [<span data-ttu-id="f27e6-119">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="f27e6-119">Metadata Enumerations</span></span>](metadata-enumerations.md)

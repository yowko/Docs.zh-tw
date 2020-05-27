---
title: IValidator::Validate 方法
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 688abd210cca193bf03c40f000b74ecb66eb8ede
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008543"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="b6ebe-102">IValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="b6ebe-102">IValidator::Validate Method</span></span>
<span data-ttu-id="b6ebe-103">驗證指定的可移植執行檔（PE）或 Microsoft 中繼語言（MSIL）檔案。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ebe-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6ebe-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ebe-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6ebe-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="b6ebe-106">在`IVEHandler`處理驗證錯誤之實例的指標。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b6ebe-107">在載入檔案之應用程式域的指標。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="b6ebe-108">在[ValidatorFlags](validatorflags-enumeration.md)值的位元組合，表示應該執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-108">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="b6ebe-109">在結束驗證之前允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="b6ebe-110">在未使用。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b6ebe-111">在字串，指定要驗證的檔案名。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="b6ebe-112">在儲存檔案之記憶體緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="b6ebe-113">在要驗證之檔案的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ebe-114">需求</span><span class="sxs-lookup"><span data-stu-id="b6ebe-114">Requirements</span></span>  
 <span data-ttu-id="b6ebe-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6ebe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ebe-116">**標頭：** IValidator .idl，IValidator。h</span><span class="sxs-lookup"><span data-stu-id="b6ebe-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="b6ebe-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6ebe-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6ebe-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ebe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

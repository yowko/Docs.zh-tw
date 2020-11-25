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
ms.openlocfilehash: 3c59114f78af1aa8705318af093e47d4f03a82ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699140"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="00362-102">IValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="00362-102">IValidator::Validate Method</span></span>

<span data-ttu-id="00362-103">驗證指定的可攜式可執行檔 (PE) 或 Microsoft 中繼語言 (MSIL) 檔。</span><span class="sxs-lookup"><span data-stu-id="00362-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00362-104">語法</span><span class="sxs-lookup"><span data-stu-id="00362-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="00362-105">參數</span><span class="sxs-lookup"><span data-stu-id="00362-105">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="00362-106">在 `IVEHandler` 處理驗證錯誤之實例的指標。</span><span class="sxs-lookup"><span data-stu-id="00362-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="00362-107">在載入檔案之應用程式域的指標。</span><span class="sxs-lookup"><span data-stu-id="00362-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="00362-108">在 [ValidatorFlags](validatorflags-enumeration.md) 值的位元組合，表示應該執行的驗證。</span><span class="sxs-lookup"><span data-stu-id="00362-108">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="00362-109">在結束驗證之前允許的錯誤數目上限。</span><span class="sxs-lookup"><span data-stu-id="00362-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="00362-110">在未使用。</span><span class="sxs-lookup"><span data-stu-id="00362-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="00362-111">在字串，指定要驗證之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="00362-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="00362-112">在儲存檔案之記憶體緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="00362-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="00362-113">在要驗證之檔案的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="00362-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00362-114">需求</span><span class="sxs-lookup"><span data-stu-id="00362-114">Requirements</span></span>  

 <span data-ttu-id="00362-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00362-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00362-116">**標頭：** IValidator .idl、IValidator。h</span><span class="sxs-lookup"><span data-stu-id="00362-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="00362-117">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="00362-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00362-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00362-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

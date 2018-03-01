---
title: "CorNativeType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6be442dd74f6a71494e140b76357be1bc9e1b747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="eacf8-102">CorNativeType 列舉</span><span class="sxs-lookup"><span data-stu-id="eacf8-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="eacf8-103">包含值，這些值描述原生 Unmanaged 類型。</span><span class="sxs-lookup"><span data-stu-id="eacf8-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eacf8-104">語法</span><span class="sxs-lookup"><span data-stu-id="eacf8-104">Syntax</span></span>  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="eacf8-105">成員</span><span class="sxs-lookup"><span data-stu-id="eacf8-105">Members</span></span>  
  
|<span data-ttu-id="eacf8-106">成員</span><span class="sxs-lookup"><span data-stu-id="eacf8-106">Member</span></span>|<span data-ttu-id="eacf8-107">描述</span><span class="sxs-lookup"><span data-stu-id="eacf8-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="eacf8-108">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="eacf8-109">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="eacf8-110">4 位元組布林值，其中 TRUE 是非零，FALSE 是零。</span><span class="sxs-lookup"><span data-stu-id="eacf8-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="eacf8-111">8 位元帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="eacf8-112">不帶正負號的 8 位元整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="eacf8-113">帶正負號的 16 位元整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="eacf8-114">不帶正負號的 16 位元整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="eacf8-115">帶正負號的 32 位元整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="eacf8-116">32 位元不帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="eacf8-117">64 位元帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="eacf8-118">不帶正負號的 64 位元整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="eacf8-119">4 位元組浮點數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="eacf8-120">8 位元組浮點數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="eacf8-121">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="eacf8-122">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="eacf8-123">數字的 COM 型別對應至 managed<xref:System.Decimal>型別。</span><span class="sxs-lookup"><span data-stu-id="eacf8-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="eacf8-124">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="eacf8-125">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="eacf8-126">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="eacf8-127">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="eacf8-128">LPSTR 的字串值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="eacf8-129">LPWSTR 的字串值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="eacf8-130">LPTSTR 的字串值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="eacf8-131">固定的系統定義的字串值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="eacf8-132">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="eacf8-133">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="eacf8-134">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="eacf8-135">原生結構值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="eacf8-136">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="eacf8-137">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="eacf8-138">固定長度的陣列值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="eacf8-139">原生的 16 位元帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="eacf8-140">原生的 16 位元不帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="eacf8-141">已過時。</span><span class="sxs-lookup"><span data-stu-id="eacf8-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="eacf8-142">使用 NATIVE_TYPE_STRUCT。</span><span class="sxs-lookup"><span data-stu-id="eacf8-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="eacf8-143">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="eacf8-144">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="eacf8-145">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="eacf8-146">視平台選取 BSTR 或 ansibstr 的功能。</span><span class="sxs-lookup"><span data-stu-id="eacf8-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="eacf8-147">2 位元組布林值，其中為 true，則為-1，FALSE 為零。</span><span class="sxs-lookup"><span data-stu-id="eacf8-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="eacf8-148">函式指標。</span><span class="sxs-lookup"><span data-stu-id="eacf8-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="eacf8-149">任何原生類型的參考。</span><span class="sxs-lookup"><span data-stu-id="eacf8-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="eacf8-150">未指定類型的成員與陣列的參考。</span><span class="sxs-lookup"><span data-stu-id="eacf8-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="eacf8-151">結構的 32 位元整數指標。</span><span class="sxs-lookup"><span data-stu-id="eacf8-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="eacf8-152">自訂封送處理器的原生型別。</span><span class="sxs-lookup"><span data-stu-id="eacf8-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="eacf8-153">這後面必須使用下列格式的字串: 「 原生型別名稱/0Custom 封送處理器會輸入 cookie 的名稱/0Optional/0"或"{原生類型 GUID} / 0Custom 封送處理器類型名稱/0Optional cookie/0"</span><span class="sxs-lookup"><span data-stu-id="eacf8-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="eacf8-154">COM Interop。</span><span class="sxs-lookup"><span data-stu-id="eacf8-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="eacf8-155">ELEMENT_TYPE_I4 與這個類型會對應至 VT_HRESULT。</span><span class="sxs-lookup"><span data-stu-id="eacf8-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="eacf8-156">原生`IInspectable`型別。</span><span class="sxs-lookup"><span data-stu-id="eacf8-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="eacf8-157">原生`HString`。</span><span class="sxs-lookup"><span data-stu-id="eacf8-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="eacf8-158">無效的值。</span><span class="sxs-lookup"><span data-stu-id="eacf8-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eacf8-159">需求</span><span class="sxs-lookup"><span data-stu-id="eacf8-159">Requirements</span></span>  
 <span data-ttu-id="eacf8-160">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eacf8-160">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eacf8-161">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="eacf8-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eacf8-162">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eacf8-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eacf8-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="eacf8-163">See Also</span></span>  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [<span data-ttu-id="eacf8-164">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="eacf8-164">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

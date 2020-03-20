---
title: IMetaDataEmit::DefineMethod 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177671"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="b301a-102">IMetaDataEmit::DefineMethod 方法</span><span class="sxs-lookup"><span data-stu-id="b301a-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="b301a-103">使用指定簽名的方法或全域函數創建定義，並將權杖返回到該方法定義。</span><span class="sxs-lookup"><span data-stu-id="b301a-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b301a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b301a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b301a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b301a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b301a-106">[在]方法`mdTypedef`的父類或父介面的權杖。</span><span class="sxs-lookup"><span data-stu-id="b301a-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="b301a-107">如果要`td`定義`mdTokenNil`全域函數，則設置為 ，設置為 。。</span><span class="sxs-lookup"><span data-stu-id="b301a-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b301a-108">[在]Unicode 中的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="b301a-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="b301a-109">[在][CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚舉的值，用於指定方法或全域函數的屬性。</span><span class="sxs-lookup"><span data-stu-id="b301a-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b301a-110">[在]方法簽名。</span><span class="sxs-lookup"><span data-stu-id="b301a-110">[in] The method signature.</span></span> <span data-ttu-id="b301a-111">簽名將保留為提供。</span><span class="sxs-lookup"><span data-stu-id="b301a-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="b301a-112">如果需要為任何參數指定其他資訊，請使用[IMetaDataEmit：：setParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b301a-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b301a-113">[在]中的`pvSigBlob`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="b301a-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="b301a-114">[在]代碼的位址。</span><span class="sxs-lookup"><span data-stu-id="b301a-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="b301a-115">[在][CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)枚舉的值，用於指定方法的實現特徵。</span><span class="sxs-lookup"><span data-stu-id="b301a-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="b301a-116">[出]成員權杖。</span><span class="sxs-lookup"><span data-stu-id="b301a-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b301a-117">備註</span><span class="sxs-lookup"><span data-stu-id="b301a-117">Remarks</span></span>  
 <span data-ttu-id="b301a-118">中繼資料 API 保證以與調用方為給定的封閉類或介面發出方法的順序保留方法，該類或介面在`td`參數中指定。</span><span class="sxs-lookup"><span data-stu-id="b301a-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="b301a-119">有關 使用`DefineMethod`和特定參數設置的其他資訊，請參閱下文。</span><span class="sxs-lookup"><span data-stu-id="b301a-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="b301a-120">V 表中的插槽</span><span class="sxs-lookup"><span data-stu-id="b301a-120">Slots in the V-table</span></span>  
 <span data-ttu-id="b301a-121">運行時使用方法定義來設置 v 表槽。</span><span class="sxs-lookup"><span data-stu-id="b301a-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="b301a-122">如果需要跳過一個或多個插槽（例如，使用 COM 介面佈局保留同位），則定義虛擬方法以佔用 v 表中的插槽或插槽;例如，使用 COM 介面佈局保留同位，則使用虛擬方法佔用 v-table 中的插槽或插槽。將`dwMethodFlags`設置為`mdRTSpecialName`[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)枚舉的值，並將名稱指定為：</span><span class="sxs-lookup"><span data-stu-id="b301a-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="b301a-123">_VtblGap\<*序數*>\<*CountOfSlots*計數\_></span><span class="sxs-lookup"><span data-stu-id="b301a-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="b301a-124">*其中序列編號*是方法的序號 *，CountOfSlots*是 v 表中要跳過的插槽數。</span><span class="sxs-lookup"><span data-stu-id="b301a-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="b301a-125">如果省略*了 CountOflots，* 則假定為 1。</span><span class="sxs-lookup"><span data-stu-id="b301a-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="b301a-126">這些虛擬方法不能從託管或非託管代碼調用，任何嘗試調用它們（從託管代碼或非託管代碼）都會生成異常。</span><span class="sxs-lookup"><span data-stu-id="b301a-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="b301a-127">它們的唯一目的是佔用運行時為 COM 集成生成的 v 表中的空間。</span><span class="sxs-lookup"><span data-stu-id="b301a-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="b301a-128">重複方法</span><span class="sxs-lookup"><span data-stu-id="b301a-128">Duplicate Methods</span></span>  
 <span data-ttu-id="b301a-129">不應定義重複的方法。</span><span class="sxs-lookup"><span data-stu-id="b301a-129">You should not define duplicate methods.</span></span> <span data-ttu-id="b301a-130">`DefineMethod`也就是說，不應使用`td`中`wzName`重複的值集調用 ， 和`pvSig`參數。</span><span class="sxs-lookup"><span data-stu-id="b301a-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="b301a-131">（這三個參數一起唯一地定義方法。</span><span class="sxs-lookup"><span data-stu-id="b301a-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="b301a-132">但是，可以使用重複的三重，前提是，對於方法定義之一，可以在`mdPrivateScope``dwMethodFlags`參數中設置位。</span><span class="sxs-lookup"><span data-stu-id="b301a-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="b301a-133">（該`mdPrivateScope`位表示編譯器不會發出對此方法定義的引用。</span><span class="sxs-lookup"><span data-stu-id="b301a-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="b301a-134">方法實現資訊</span><span class="sxs-lookup"><span data-stu-id="b301a-134">Method Implementation Information</span></span>  
 <span data-ttu-id="b301a-135">在聲明方法時，通常不知道有關方法實現的資訊。</span><span class="sxs-lookup"><span data-stu-id="b301a-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="b301a-136">因此，調用 時不需要傳遞`ulCodeRVA`和`dwImplFlags`參數中的值。 `DefineMethod`</span><span class="sxs-lookup"><span data-stu-id="b301a-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="b301a-137">這些值稍後可以通過[IMetaDataEmit：：設置方法Implflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或[IMetaDataEmit：：SetRVA，](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)視情況而定。</span><span class="sxs-lookup"><span data-stu-id="b301a-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="b301a-138">在某些情況下，如平台叫用 （PInvoke） 或 COM 互通方案，將不會提供方法正文，並且`ulCodeRVA`應設置為零。</span><span class="sxs-lookup"><span data-stu-id="b301a-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="b301a-139">在這些情況下，方法不應標記為抽象，因為運行時將定位實現。</span><span class="sxs-lookup"><span data-stu-id="b301a-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="b301a-140">定義 PInvoke 的方法</span><span class="sxs-lookup"><span data-stu-id="b301a-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="b301a-141">要通過 PInvoke 調用每個非託管函數，必須定義表示目標非託管函數的託管方法。</span><span class="sxs-lookup"><span data-stu-id="b301a-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="b301a-142">要定義託管方法，請使用`DefineMethod`設置為特定值的某些參數，具體取決於 PInvoke 的使用方式：</span><span class="sxs-lookup"><span data-stu-id="b301a-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="b301a-143">True PInvoke - 涉及調用駐留在非託管 DLL 中的外部非託管方法。</span><span class="sxs-lookup"><span data-stu-id="b301a-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="b301a-144">本地 PInvoke - 涉及調用嵌入在當前託管模組中的本機非託管方法。</span><span class="sxs-lookup"><span data-stu-id="b301a-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="b301a-145">參數設置在下表中給出。</span><span class="sxs-lookup"><span data-stu-id="b301a-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="b301a-146">參數</span><span class="sxs-lookup"><span data-stu-id="b301a-146">Parameter</span></span>|<span data-ttu-id="b301a-147">真實 PInvoke 的值</span><span class="sxs-lookup"><span data-stu-id="b301a-147">Values for true PInvoke</span></span>|<span data-ttu-id="b301a-148">本地 PInvoke 的值</span><span class="sxs-lookup"><span data-stu-id="b301a-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="b301a-149">設置`mdStatic`;清楚`mdSynchronized`和`mdAbstract`。</span><span class="sxs-lookup"><span data-stu-id="b301a-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="b301a-150">有效的通用語言運行時 （CLR） 方法簽名，具有有效的託管類型的參數。</span><span class="sxs-lookup"><span data-stu-id="b301a-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="b301a-151">具有有效託管類型的參數的有效 CLR 方法簽名。</span><span class="sxs-lookup"><span data-stu-id="b301a-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="b301a-152">0</span><span class="sxs-lookup"><span data-stu-id="b301a-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="b301a-153">請設定 `miCil` 和 `miManaged`。</span><span class="sxs-lookup"><span data-stu-id="b301a-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="b301a-154">請設定 `miNative` 和 `miUnmanaged`。</span><span class="sxs-lookup"><span data-stu-id="b301a-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b301a-155">需求</span><span class="sxs-lookup"><span data-stu-id="b301a-155">Requirements</span></span>  
 <span data-ttu-id="b301a-156">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b301a-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b301a-157">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="b301a-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b301a-158">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b301a-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b301a-159">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b301a-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b301a-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b301a-160">See also</span></span>

- [<span data-ttu-id="b301a-161">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b301a-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b301a-162">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b301a-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

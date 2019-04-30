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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a67e8ce19a2acf5b4ee1d114858e00d93cb183b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044129"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="16a0f-102">IMetaDataEmit::DefineMethod 方法</span><span class="sxs-lookup"><span data-stu-id="16a0f-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="16a0f-103">使用指定的簽章中，建立方法或全域函式的定義，並將權杖傳回給該方法的定義。</span><span class="sxs-lookup"><span data-stu-id="16a0f-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a0f-104">語法</span><span class="sxs-lookup"><span data-stu-id="16a0f-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="16a0f-105">參數</span><span class="sxs-lookup"><span data-stu-id="16a0f-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="16a0f-106">[in]`mdTypedef`語彙基元的父類別或方法的父介面。</span><span class="sxs-lookup"><span data-stu-id="16a0f-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="16a0f-107">設定`td`至`mdTokenNil`，如果您正在定義全域函式。</span><span class="sxs-lookup"><span data-stu-id="16a0f-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="16a0f-108">[in]以 Unicode 成員名稱。</span><span class="sxs-lookup"><span data-stu-id="16a0f-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="16a0f-109">[in]值為[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉，指定方法或全域函式的屬性。</span><span class="sxs-lookup"><span data-stu-id="16a0f-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="16a0f-110">[in]方法簽章。</span><span class="sxs-lookup"><span data-stu-id="16a0f-110">[in] The method signature.</span></span> <span data-ttu-id="16a0f-111">提供，則會保存簽章。</span><span class="sxs-lookup"><span data-stu-id="16a0f-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="16a0f-112">如果您需要指定任何參數的其他資訊，請使用[imetadataemit:: Setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="16a0f-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="16a0f-113">[in]中的位元組計數`pvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="16a0f-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="16a0f-114">[in]程式碼的位址。</span><span class="sxs-lookup"><span data-stu-id="16a0f-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="16a0f-115">[in]值為[CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)列舉，指定方法的實作功能。</span><span class="sxs-lookup"><span data-stu-id="16a0f-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="16a0f-116">[out]成員語彙基元。</span><span class="sxs-lookup"><span data-stu-id="16a0f-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16a0f-117">備註</span><span class="sxs-lookup"><span data-stu-id="16a0f-117">Remarks</span></span>  
 <span data-ttu-id="16a0f-118">保存方法的相同順序，因為呼叫端會將它們發出指定封入類別或介面中所指定的中繼資料 API 可保證`td`參數。</span><span class="sxs-lookup"><span data-stu-id="16a0f-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="16a0f-119">使用有關的其他資訊`DefineMethod`和特定的參數設定如下。</span><span class="sxs-lookup"><span data-stu-id="16a0f-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="16a0f-120">V 資料表中的位置</span><span class="sxs-lookup"><span data-stu-id="16a0f-120">Slots in the V-table</span></span>  
 <span data-ttu-id="16a0f-121">執行階段會使用方法定義，來設定 v-table 位置。</span><span class="sxs-lookup"><span data-stu-id="16a0f-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="16a0f-122">在其中一個或多個位置需要略過，這類情況下對於保留同位檢查 COM 介面的版面配置，虛擬方法定義為佔用的位置或 v-table; 中的位置設定`dwMethodFlags`要`mdRTSpecialName`的值[CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉型別並將名稱指定為：</span><span class="sxs-lookup"><span data-stu-id="16a0f-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="16a0f-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="16a0f-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="16a0f-124">何處*SequenceNumber*是方法的序號和*CountOfSlots*會在 v-table 中略過的位置數目。</span><span class="sxs-lookup"><span data-stu-id="16a0f-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="16a0f-125">如果*CountOfSlots*已省略，則假設為 1。</span><span class="sxs-lookup"><span data-stu-id="16a0f-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="16a0f-126">這些虛擬方法不是可從 managed 或 unmanaged 程式碼呼叫，任何嘗試呼叫它們，從 managed 或 unmanaged 程式碼，就會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="16a0f-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="16a0f-127">其唯一用途是佔用執行階段會產生 COM 整合 v 資料表中的空間。</span><span class="sxs-lookup"><span data-stu-id="16a0f-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="16a0f-128">重複的方法</span><span class="sxs-lookup"><span data-stu-id="16a0f-128">Duplicate Methods</span></span>  
 <span data-ttu-id="16a0f-129">您不能定義重複的方法。</span><span class="sxs-lookup"><span data-stu-id="16a0f-129">You should not define duplicate methods.</span></span> <span data-ttu-id="16a0f-130">也就是說，您不應該呼叫`DefineMethod`與一組重複的值`td`， `wzName`，和`pvSig`參數。</span><span class="sxs-lookup"><span data-stu-id="16a0f-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="16a0f-131">(這三個參數一起唯一定義的方法。)。</span><span class="sxs-lookup"><span data-stu-id="16a0f-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="16a0f-132">不過，使用重複的三倍，前提是，在您設定的其中一個方法定義，`mdPrivateScope`位元`dwMethodFlags`參數。</span><span class="sxs-lookup"><span data-stu-id="16a0f-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="16a0f-133">(`mdPrivateScope`位元表示編譯器將不會發出這個方法定義的參考。)</span><span class="sxs-lookup"><span data-stu-id="16a0f-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="16a0f-134">方法的實作資訊</span><span class="sxs-lookup"><span data-stu-id="16a0f-134">Method Implementation Information</span></span>  
 <span data-ttu-id="16a0f-135">在此方法宣告的時間通常不知道方法實作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="16a0f-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="16a0f-136">因此，您不需要傳遞值`ulCodeRVA`並`dwImplFlags`參數呼叫時`DefineMethod`。</span><span class="sxs-lookup"><span data-stu-id="16a0f-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="16a0f-137">提供值的順序可以稍後透過[imetadataemit:: Setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)或是[imetadataemit:: Setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)視需要。</span><span class="sxs-lookup"><span data-stu-id="16a0f-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="16a0f-138">在某些情況下，例如平台叫用 (PInvoke) 或 COM interop 案例中，不會提供方法主體，以及`ulCodeRVA`應該設定為零。</span><span class="sxs-lookup"><span data-stu-id="16a0f-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="16a0f-139">在這些情況下，此方法不應標記為抽象，因為執行階段會找出實作。</span><span class="sxs-lookup"><span data-stu-id="16a0f-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="16a0f-140">定義方法的 PInvoke</span><span class="sxs-lookup"><span data-stu-id="16a0f-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="16a0f-141">對於透過 PInvoke 呼叫每個 unmanaged 函式，您必須定義受管理的方法，表示目標 unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="16a0f-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="16a0f-142">若要定義受管理的方法，使用`DefineMethod`與某些參數設為特定值，根據在其中使用 PInvoke 的方式：</span><span class="sxs-lookup"><span data-stu-id="16a0f-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="16a0f-143">True PInvoke-涉及在 unmanaged DLL 位於外部的 unmanaged 方法引動過程。</span><span class="sxs-lookup"><span data-stu-id="16a0f-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="16a0f-144">本機 PInvoke-包含內嵌於目前的受管理模組中的原生 unmanaged 方法的引動過程。</span><span class="sxs-lookup"><span data-stu-id="16a0f-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="16a0f-145">下表提供的參數設定。</span><span class="sxs-lookup"><span data-stu-id="16a0f-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="16a0f-146">參數</span><span class="sxs-lookup"><span data-stu-id="16a0f-146">Parameter</span></span>|<span data-ttu-id="16a0f-147">值，則為 true 的 PInvoke</span><span class="sxs-lookup"><span data-stu-id="16a0f-147">Values for true PInvoke</span></span>|<span data-ttu-id="16a0f-148">本機 PInvoke 的值</span><span class="sxs-lookup"><span data-stu-id="16a0f-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="16a0f-149">設定`mdStatic`; 清除`mdSynchronized`和`mdAbstract`。</span><span class="sxs-lookup"><span data-stu-id="16a0f-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="16a0f-150">有效 common language runtime (CLR) 方法簽章具有有效的參數將 managed 型别。</span><span class="sxs-lookup"><span data-stu-id="16a0f-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="16a0f-151">有效的 CLR 方法簽章，以有效的參數將 managed 型别。</span><span class="sxs-lookup"><span data-stu-id="16a0f-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="16a0f-152">0</span><span class="sxs-lookup"><span data-stu-id="16a0f-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="16a0f-153">設定`miCil`和`miManaged`。</span><span class="sxs-lookup"><span data-stu-id="16a0f-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="16a0f-154">設定`miNative`和`miUnmanaged`。</span><span class="sxs-lookup"><span data-stu-id="16a0f-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16a0f-155">需求</span><span class="sxs-lookup"><span data-stu-id="16a0f-155">Requirements</span></span>  
 <span data-ttu-id="16a0f-156">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16a0f-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16a0f-157">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16a0f-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16a0f-158">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="16a0f-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16a0f-159">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16a0f-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a0f-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16a0f-160">See also</span></span>

- [<span data-ttu-id="16a0f-161">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="16a0f-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="16a0f-162">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="16a0f-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

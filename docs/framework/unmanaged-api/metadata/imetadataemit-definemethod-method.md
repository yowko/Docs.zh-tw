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
ms.openlocfilehash: a32a1eb850943b84a0d368f883e44fd4ccf32ee9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719576"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="90725-102">IMetaDataEmit::DefineMethod 方法</span><span class="sxs-lookup"><span data-stu-id="90725-102">IMetaDataEmit::DefineMethod Method</span></span>

<span data-ttu-id="90725-103">使用指定的簽章來建立方法或全域函式的定義，並將標記傳回至該方法定義。</span><span class="sxs-lookup"><span data-stu-id="90725-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90725-104">語法</span><span class="sxs-lookup"><span data-stu-id="90725-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="90725-105">參數</span><span class="sxs-lookup"><span data-stu-id="90725-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="90725-106">在 `mdTypedef` 方法的父類別或父介面的標記。</span><span class="sxs-lookup"><span data-stu-id="90725-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="90725-107">`td` `mdTokenNil` 如果您要定義全域函數，請將設定為。</span><span class="sxs-lookup"><span data-stu-id="90725-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="90725-108">在Unicode 中的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="90725-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="90725-109">在 [CorMethodAttr](cormethodattr-enumeration.md) 列舉的值，可指定方法或全域函式的屬性。</span><span class="sxs-lookup"><span data-stu-id="90725-109">[in] A value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="90725-110">在方法簽章。</span><span class="sxs-lookup"><span data-stu-id="90725-110">[in] The method signature.</span></span> <span data-ttu-id="90725-111">簽章會依照提供的方式保存。</span><span class="sxs-lookup"><span data-stu-id="90725-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="90725-112">如果您需要指定任何參數的其他資訊，請使用 [IMetaDataEmit：： SetParamProps](imetadataemit-setparamprops-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="90725-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="90725-113">在中的位元組計數 `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="90725-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="90725-114">在程式碼的位址。</span><span class="sxs-lookup"><span data-stu-id="90725-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="90725-115">在 [CorMethodImpl](cormethodimpl-enumeration.md) 列舉的值，可指定方法的執行功能。</span><span class="sxs-lookup"><span data-stu-id="90725-115">[in] A value of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="90725-116">擴展成員 token。</span><span class="sxs-lookup"><span data-stu-id="90725-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90725-117">備註</span><span class="sxs-lookup"><span data-stu-id="90725-117">Remarks</span></span>  

 <span data-ttu-id="90725-118">中繼資料 API 可保證保存方法的順序，與呼叫者針對指定的封閉類別或介面（在參數中所指定）發出時相同 `td` 。</span><span class="sxs-lookup"><span data-stu-id="90725-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="90725-119">`DefineMethod`以下提供有關使用和特定參數設定的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="90725-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="90725-120">V 資料表中的插槽</span><span class="sxs-lookup"><span data-stu-id="90725-120">Slots in the V-table</span></span>  

 <span data-ttu-id="90725-121">執行時間會使用方法定義來設定 v 資料表的位置。</span><span class="sxs-lookup"><span data-stu-id="90725-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="90725-122">在需要略過一或多個位置的情況下（例如，為了保留與 COM 介面配置的同位），會定義虛擬方法，以佔用 v 資料表中的位置或插槽;將設定 `dwMethodFlags` 為 `mdRTSpecialName` [CorMethodAttr](cormethodattr-enumeration.md) 列舉的值，並將名稱指定為：</span><span class="sxs-lookup"><span data-stu-id="90725-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="90725-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="90725-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="90725-124">其中 *SequenceNumber* 是方法的序號，而 *CountOfSlots* 是要在 v 資料表中略過的位置數目。</span><span class="sxs-lookup"><span data-stu-id="90725-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="90725-125">如果省略 *CountOfSlots* ，則會假設為1。</span><span class="sxs-lookup"><span data-stu-id="90725-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="90725-126">這些虛擬方法無法從 managed 或非受控碼進行呼叫，而且任何從 managed 或非受控碼呼叫它們的嘗試都會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="90725-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="90725-127">其唯一目的是要佔用執行時間為 COM 整合所產生之 v 資料表中的空間。</span><span class="sxs-lookup"><span data-stu-id="90725-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="90725-128">重複的方法</span><span class="sxs-lookup"><span data-stu-id="90725-128">Duplicate Methods</span></span>  

 <span data-ttu-id="90725-129">您不應該定義重複的方法。</span><span class="sxs-lookup"><span data-stu-id="90725-129">You should not define duplicate methods.</span></span> <span data-ttu-id="90725-130">也就是說，您不應該 `DefineMethod` 使用 `td` 、和參數中的一組重複值來呼叫 `wzName` `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="90725-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="90725-131"> (這三個參數一起唯一定義方法。 ) 。</span><span class="sxs-lookup"><span data-stu-id="90725-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="90725-132">不過，您可以使用重複的三重，在其中一個方法定義中，您可以 `mdPrivateScope` 在參數中設定位 `dwMethodFlags` 。</span><span class="sxs-lookup"><span data-stu-id="90725-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="90725-133"> (`mdPrivateScope` 位表示編譯器將不會發出此方法定義的參考。 ) </span><span class="sxs-lookup"><span data-stu-id="90725-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="90725-134">方法執行資訊</span><span class="sxs-lookup"><span data-stu-id="90725-134">Method Implementation Information</span></span>  

 <span data-ttu-id="90725-135">在宣告方法時，通常不知道方法執行的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="90725-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="90725-136">因此，當您呼叫時，不需要在和參數中傳遞值 `ulCodeRVA` `dwImplFlags` `DefineMethod` 。</span><span class="sxs-lookup"><span data-stu-id="90725-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="90725-137">您可以視需要透過 [IMetaDataEmit：： SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) 或 [IMetaDataEmit：： SetRVA](imetadataemit-setrva-method.md)提供這些值。</span><span class="sxs-lookup"><span data-stu-id="90725-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="90725-138">在某些情況下（例如平台叫用） (PInvoke) 或 COM interop 案例中，將不會提供方法主體，而且 `ulCodeRVA` 應設為零。</span><span class="sxs-lookup"><span data-stu-id="90725-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="90725-139">在這些情況下，方法不應標記為抽象，因為執行時間會找出執行。</span><span class="sxs-lookup"><span data-stu-id="90725-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="90725-140">定義 PInvoke 的方法</span><span class="sxs-lookup"><span data-stu-id="90725-140">Defining a Method for PInvoke</span></span>  

 <span data-ttu-id="90725-141">針對透過 PInvoke 呼叫的每個非受控函式，您必須定義表示目標未受管理函數的 managed 方法。</span><span class="sxs-lookup"><span data-stu-id="90725-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="90725-142">若要定義 managed 方法，請使用， `DefineMethod` 並將某些參數設為特定值，視使用 PInvoke 的方式而定：</span><span class="sxs-lookup"><span data-stu-id="90725-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="90725-143">True PInvoke-牽涉到位於非受控 DLL 中的外部非受控方法的調用。</span><span class="sxs-lookup"><span data-stu-id="90725-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="90725-144">Local PInvoke-牽涉到內嵌于目前受管理模組中的原生非受控方法的調用。</span><span class="sxs-lookup"><span data-stu-id="90725-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="90725-145">下表提供參數設定。</span><span class="sxs-lookup"><span data-stu-id="90725-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="90725-146">參數</span><span class="sxs-lookup"><span data-stu-id="90725-146">Parameter</span></span>|<span data-ttu-id="90725-147">True PInvoke 的值</span><span class="sxs-lookup"><span data-stu-id="90725-147">Values for true PInvoke</span></span>|<span data-ttu-id="90725-148">本機 PInvoke 的值</span><span class="sxs-lookup"><span data-stu-id="90725-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="90725-149">Set `mdStatic` ; clear `mdSynchronized` 和 `mdAbstract` 。</span><span class="sxs-lookup"><span data-stu-id="90725-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="90725-150">有效的 common language runtime (CLR) 方法簽章，其參數為有效的 managed 類型。</span><span class="sxs-lookup"><span data-stu-id="90725-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="90725-151">具有有效 managed 類型之參數的有效 CLR 方法簽章。</span><span class="sxs-lookup"><span data-stu-id="90725-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="90725-152">0</span><span class="sxs-lookup"><span data-stu-id="90725-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="90725-153">請設定 `miCil` 和 `miManaged`。</span><span class="sxs-lookup"><span data-stu-id="90725-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="90725-154">請設定 `miNative` 和 `miUnmanaged`。</span><span class="sxs-lookup"><span data-stu-id="90725-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90725-155">需求</span><span class="sxs-lookup"><span data-stu-id="90725-155">Requirements</span></span>  

 <span data-ttu-id="90725-156">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90725-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90725-157">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="90725-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90725-158">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="90725-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90725-159">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90725-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90725-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90725-160">See also</span></span>

- [<span data-ttu-id="90725-161">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="90725-161">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="90725-162">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="90725-162">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

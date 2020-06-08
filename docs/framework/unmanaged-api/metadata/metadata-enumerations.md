---
title: 中繼資料列舉
ms.date: 03/30/2017
helpviewer_keywords:
- enumerations [.NET Framework metadata]
- metadata enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], metadata
ms.assetid: 711ab251-cfdb-4280-aaa6-9bc1b341cdc3
ms.openlocfilehash: 2409998c53aee8cb76e66cbc9a6cd92ad9fb6cd2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489617"
---
# <a name="metadata-enumerations"></a><span data-ttu-id="70af9-102">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-102">Metadata Enumerations</span></span>
<span data-ttu-id="70af9-103">本節描述中繼資料應用程式開發介面所使用的 Unmanaged 列舉。</span><span class="sxs-lookup"><span data-stu-id="70af9-103">This section describes the unmanaged enumerations that the metadata API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70af9-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="70af9-104">In This Section</span></span>  
 [<span data-ttu-id="70af9-105">AssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-105">AssemblyFlags Enumeration</span></span>](assemblyflags-enumeration.md)  
 <span data-ttu-id="70af9-106">包含值，這些值描述組件的執行階段功能。</span><span class="sxs-lookup"><span data-stu-id="70af9-106">Contains values that describe the run-time features of an assembly.</span></span>  
  
 [<span data-ttu-id="70af9-107">AssemblyRefFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-107">AssemblyRefFlags Enumeration</span></span>](assemblyrefflags-enumeration.md)  
 <span data-ttu-id="70af9-108">包含值，這些值描述組件參考的功能。</span><span class="sxs-lookup"><span data-stu-id="70af9-108">Contains values that describe the features of an assembly reference.</span></span>  
  
 [<span data-ttu-id="70af9-109">CeeSectionAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-109">CeeSectionAttr Enumeration</span></span>](ceesectionattr-enumeration.md)  
 <span data-ttu-id="70af9-110">提供值，指定區段的屬性，以供[ICeeGen](iceegen-interface.md)介面使用。</span><span class="sxs-lookup"><span data-stu-id="70af9-110">Provides values that specify the attributes of a section for use by the [ICeeGen](iceegen-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="70af9-111">CeeSectionRelocType 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-111">CeeSectionRelocType Enumeration</span></span>](ceesectionreloctype-enumeration.md)  
 <span data-ttu-id="70af9-112">提供值，以影響 `reloc` 呼叫[ICeeGen：： AddSectionReloc](iceegen-addsectionreloc-method.md)方法時所發出的指令類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-112">Provides values to influence the type of `reloc` instruction emitted in a call to the [ICeeGen::AddSectionReloc](iceegen-addsectionreloc-method.md) method.</span></span>  
  
 [<span data-ttu-id="70af9-113">COINITICOR 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-113">COINITICOR Enumeration</span></span>](coiniticor-enumeration.md)  
 <span data-ttu-id="70af9-114">指定初始化 common language runtime 時， [CoInitializeCor](../hosting/coinitializecor-function.md)所使用的常數。</span><span class="sxs-lookup"><span data-stu-id="70af9-114">Specifies constants used by [CoInitializeCor](../hosting/coinitializecor-function.md) when initializing the common language runtime.</span></span>  
  
 [<span data-ttu-id="70af9-115">COINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-115">COINITIEE Enumeration</span></span>](coinitiee-enumeration.md)  
 <span data-ttu-id="70af9-116">指定初始化 common language runtime 時， [CoInitializeEE](../hosting/coinitializeee-function.md)所使用的常數。</span><span class="sxs-lookup"><span data-stu-id="70af9-116">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
 [<span data-ttu-id="70af9-117">CorArgType 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-117">CorArgType Enumeration</span></span>](corargtype-enumeration.md)  
 <span data-ttu-id="70af9-118">包含值，這些值描述執行階段控制代碼的原生類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-118">Contains values that describe the native type of a runtime handle.</span></span>  
  
 [<span data-ttu-id="70af9-119">CorAssemblyFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-119">CorAssemblyFlags Enumeration</span></span>](corassemblyflags-enumeration.md)  
 <span data-ttu-id="70af9-120">包含值，這些值描述套用至組件編譯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70af9-120">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
 [<span data-ttu-id="70af9-121">CorAttributeTargets 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-121">CorAttributeTargets Enumeration</span></span>](corattributetargets-enumeration.md)  
 <span data-ttu-id="70af9-122">指定有效套用屬性的應用程式項目。</span><span class="sxs-lookup"><span data-stu-id="70af9-122">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
 [<span data-ttu-id="70af9-123">CorCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-123">CorCallingConvention Enumeration</span></span>](corcallingconvention-enumeration.md)  
 <span data-ttu-id="70af9-124">包含值，這些值描述在 Managed 程式碼中進行的呼叫慣例類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-124">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
 [<span data-ttu-id="70af9-125">CorCheckDuplicatesFor 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-125">CorCheckDuplicatesFor Enumeration</span></span>](corcheckduplicatesfor-enumeration.md)  
 <span data-ttu-id="70af9-126">包含值，可在檢查期間用來檢查是否有重複項目。</span><span class="sxs-lookup"><span data-stu-id="70af9-126">Contains values used during checks for duplications.</span></span>  
  
 [<span data-ttu-id="70af9-127">CorDeclSecurity 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-127">CorDeclSecurity Enumeration</span></span>](cordeclsecurity-enumeration.md)  
 <span data-ttu-id="70af9-128">包含值，這些值描述 Common Language Runtime 所使用的宣告式安全性類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-128">Contains values that describe the types of declarative security used by the common language runtime.</span></span>  
  
 <span data-ttu-id="70af9-129">CorElementType</span><span class="sxs-lookup"><span data-stu-id="70af9-129">CorElementType</span></span>  
 <span data-ttu-id="70af9-130">包含值，這些值描述 Common Language Runtime <xref:System.Type> 的基礎原生類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-130">Contains values that describe the underlying native type of a common language runtime <xref:System.Type>.</span></span>  
  
 [<span data-ttu-id="70af9-131">CorErrorIfEmitOutOfOrder 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-131">CorErrorIfEmitOutOfOrder Enumeration</span></span>](corerrorifemitoutoforder-enumeration.md)  
 <span data-ttu-id="70af9-132">包含旗標值，這些值表示中繼資料未按順序發出時，在哪些條件下應該產生錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="70af9-132">Contains flag values that indicate the conditions under which an error message should be generated when metadata is emitted out of order.</span></span>  
  
 [<span data-ttu-id="70af9-133">CorEventAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-133">CorEventAttr Enumeration</span></span>](coreventattr-enumeration.md)  
 <span data-ttu-id="70af9-134">包含值，這些值描述事件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70af9-134">Contains values that describe the metadata of an event.</span></span>  
  
 [<span data-ttu-id="70af9-135">CorFieldAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-135">CorFieldAttr Enumeration</span></span>](corfieldattr-enumeration.md)  
 <span data-ttu-id="70af9-136">包含值，這些值描述與欄位有關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70af9-136">Contains values that describe metadata about a field.</span></span>  
  
 [<span data-ttu-id="70af9-137">CorFileFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-137">CorFileFlags Enumeration</span></span>](corfileflags-enumeration.md)  
 <span data-ttu-id="70af9-138">包含值，描述在[IMetaDataAssemblyEmit：:D efinefile](imetadataassemblyemit-definefile-method.md)方法的呼叫中定義的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-138">Contains values that describe the type of file defined in a call to the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
 [<span data-ttu-id="70af9-139">CorFileMapping 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-139">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)  
 <span data-ttu-id="70af9-140">包含值，描述從[IMetaDataInfo：： GetFileMapping](imetadatainfo-getfilemapping-method.md)方法的呼叫所傳回的檔對應類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-140">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
 [<span data-ttu-id="70af9-141">CorGenericParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-141">CorGenericParamAttr Enumeration</span></span>](corgenericparamattr-enumeration.md)  
 <span data-ttu-id="70af9-142">包含值，描述 <xref:System.Type> 泛型型別的參數，如同[IMetaDataEmit2：:D efinegenericparam](imetadataemit2-definegenericparam-method.md)方法的呼叫中所使用。</span><span class="sxs-lookup"><span data-stu-id="70af9-142">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to the [IMetaDataEmit2::DefineGenericParam](imetadataemit2-definegenericparam-method.md) method.</span></span>  
  
 [<span data-ttu-id="70af9-143">CorImportOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-143">CorImportOptions Enumeration</span></span>](corimportoptions-enumeration.md)  
 <span data-ttu-id="70af9-144">包含旗標值，這些值可控制在匯入目前範圍之外的組件期間所發生的行為。</span><span class="sxs-lookup"><span data-stu-id="70af9-144">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
 [<span data-ttu-id="70af9-145">CorLinkerOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-145">CorLinkerOptions Enumeration</span></span>](corlinkeroptions-enumeration.md)  
 <span data-ttu-id="70af9-146">指定旗標，以選取中繼資料連結器的選項。</span><span class="sxs-lookup"><span data-stu-id="70af9-146">Specifies flags to select options for the metadata linker.</span></span>  
  
 [<span data-ttu-id="70af9-147">CorLocalRefPreservation 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-147">CorLocalRefPreservation Enumeration</span></span>](corlocalrefpreservation-enumeration.md)  
 <span data-ttu-id="70af9-148">包含代表本機參考處理方式的旗標值。</span><span class="sxs-lookup"><span data-stu-id="70af9-148">Contains flag values for the treatment of local references.</span></span>  
  
 [<span data-ttu-id="70af9-149">CorManifestResourceFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-149">CorManifestResourceFlags Enumeration</span></span>](cormanifestresourceflags-enumeration.md)  
 <span data-ttu-id="70af9-150">包含值，這些值描述編碼在組件資訊清單中的資源可視性。</span><span class="sxs-lookup"><span data-stu-id="70af9-150">Contains values that describe the visibility of resources encoded in an assembly manifest.</span></span>  
  
 [<span data-ttu-id="70af9-151">CorMethodAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-151">CorMethodAttr Enumeration</span></span>](cormethodattr-enumeration.md)  
 <span data-ttu-id="70af9-152">包含值，這些值描述與方法有關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70af9-152">Contains values that describe metadata about a method.</span></span>  
  
 [<span data-ttu-id="70af9-153">CorMethodImpl 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-153">CorMethodImpl Enumeration</span></span>](cormethodimpl-enumeration.md)  
 <span data-ttu-id="70af9-154">包含值，這些值描述方法實作功能。</span><span class="sxs-lookup"><span data-stu-id="70af9-154">Contains values that describe method implementation features.</span></span>  
  
 [<span data-ttu-id="70af9-155">CorMethodSemanticsAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-155">CorMethodSemanticsAttr Enumeration</span></span>](cormethodsemanticsattr-enumeration.md)  
 <span data-ttu-id="70af9-156">包含值，這些值描述方法與關聯的屬性或事件之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="70af9-156">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
 [<span data-ttu-id="70af9-157">CorNativeLinkFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-157">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)  
 <span data-ttu-id="70af9-158">提供連結器在連結機器碼時所使用的旗標值。</span><span class="sxs-lookup"><span data-stu-id="70af9-158">Provides flag values used by the linker when linking native code.</span></span>  
  
 [<span data-ttu-id="70af9-159">CorNativeLinkType 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-159">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)  
 <span data-ttu-id="70af9-160">提供值，這些值表示機器碼中已連結的類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-160">Provides values that indicate the type linked in native code.</span></span>  
  
 [<span data-ttu-id="70af9-161">CorNativeType 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-161">CorNativeType Enumeration</span></span>](cornativetype-enumeration.md)  
 <span data-ttu-id="70af9-162">包含值，這些值描述原生 Unmanaged 類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-162">Contains values that describe native unmanaged types.</span></span>  
  
 [<span data-ttu-id="70af9-163">CorNotificationForTokenMovement 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-163">CorNotificationForTokenMovement Enumeration</span></span>](cornotificationfortokenmovement-enumeration.md)  
 <span data-ttu-id="70af9-164">包含旗標值，這些值會影響語彙基元移動時的通知。</span><span class="sxs-lookup"><span data-stu-id="70af9-164">Contains flag values that influence notifications upon token movement.</span></span>  
  
 [<span data-ttu-id="70af9-165">CorOpenFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-165">CorOpenFlags Enumeration</span></span>](coropenflags-enumeration.md)  
 <span data-ttu-id="70af9-166">包含在開啟資訊清單檔案時控制中繼資料行為的旗標值。</span><span class="sxs-lookup"><span data-stu-id="70af9-166">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
 [<span data-ttu-id="70af9-167">CorParamAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-167">CorParamAttr Enumeration</span></span>](corparamattr-enumeration.md)  
 <span data-ttu-id="70af9-168">包含值，這些值描述方法參數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70af9-168">Contains values that describe the metadata of a method parameter.</span></span>  
  
 [<span data-ttu-id="70af9-169">CorPEKind 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-169">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)  
 <span data-ttu-id="70af9-170">包含值，描述從[IMetaDataImport2：： GetPEKind](imetadataimport2-getpekind-method.md)方法的呼叫傳回的可攜式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="70af9-170">Contains values that describe a portable executable file, as returned from a call to the [IMetaDataImport2::GetPEKind](imetadataimport2-getpekind-method.md) method.</span></span>  
  
 [<span data-ttu-id="70af9-171">CorPinvokeMap 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-171">CorPinvokeMap Enumeration</span></span>](corpinvokemap-enumeration.md)  
 <span data-ttu-id="70af9-172">包含值，這些值會描述 PInvoke 呼叫的功能。</span><span class="sxs-lookup"><span data-stu-id="70af9-172">Contains values that describe features of a PInvoke call.</span></span>  
  
 [<span data-ttu-id="70af9-173">CorPropertyAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-173">CorPropertyAttr Enumeration</span></span>](corpropertyattr-enumeration.md)  
 <span data-ttu-id="70af9-174">包含值，這些值描述屬性的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70af9-174">Contains values that describe the metadata of a property.</span></span>  
  
 [<span data-ttu-id="70af9-175">CorRefToDefCheck 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-175">CorRefToDefCheck Enumeration</span></span>](correftodefcheck-enumeration.md)  
 <span data-ttu-id="70af9-176">指定旗標，以控制哪些參考的項目已轉換成其定義，以便最佳化程式碼。</span><span class="sxs-lookup"><span data-stu-id="70af9-176">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
 [<span data-ttu-id="70af9-177">CorRegFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-177">CorRegFlags Enumeration</span></span>](corregflags-enumeration.md)  
 <span data-ttu-id="70af9-178">提供安裝模組或組合時，用於註冊的旗標值。</span><span class="sxs-lookup"><span data-stu-id="70af9-178">Provides flag values used for registration when installing a module or composite.</span></span>  
  
 [<span data-ttu-id="70af9-179">CorSaveSize 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-179">CorSaveSize Enumeration</span></span>](corsavesize-enumeration.md)  
 <span data-ttu-id="70af9-180">包含值，這些值表示在查詢儲存作業的大小時所需的精確度等級。</span><span class="sxs-lookup"><span data-stu-id="70af9-180">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
 [<span data-ttu-id="70af9-181">CorSerializationType 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-181">CorSerializationType Enumeration</span></span>](corserializationtype-enumeration.md)  
 <span data-ttu-id="70af9-182">包含值，這些值描述 Common Language Runtime 如何將物件序列化。</span><span class="sxs-lookup"><span data-stu-id="70af9-182">Contains values that describe how an object is serialized by the common language runtime.</span></span> <span data-ttu-id="70af9-183">這些值通常會對應至 CorElementType 值。</span><span class="sxs-lookup"><span data-stu-id="70af9-183">These values generally correspond to CorElementType values.</span></span>  
  
 [<span data-ttu-id="70af9-184">CorSetENC 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-184">CorSetENC Enumeration</span></span>](corsetenc-enumeration.md)  
 <span data-ttu-id="70af9-185">包含值，可用來在中繼資料產生期間影響行為。</span><span class="sxs-lookup"><span data-stu-id="70af9-185">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
 [<span data-ttu-id="70af9-186">CorThreadSafetyOptions 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-186">CorThreadSafetyOptions Enumeration</span></span>](corthreadsafetyoptions-enumeration.md)  
 <span data-ttu-id="70af9-187">指定旗標，以選取執行緒安全的選項。</span><span class="sxs-lookup"><span data-stu-id="70af9-187">Specifies flags to select options for thread safety.</span></span>  
  
 [<span data-ttu-id="70af9-188">CorTokenType 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-188">CorTokenType Enumeration</span></span>](cortokentype-enumeration.md)  
 <span data-ttu-id="70af9-189">包含值，這些值表示中繼資料語彙基元所參考的物件類型。</span><span class="sxs-lookup"><span data-stu-id="70af9-189">Contains values that indicate the kind of object that a metadata token references.</span></span>  
  
 [<span data-ttu-id="70af9-190">CorTypeAttr 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-190">CorTypeAttr Enumeration</span></span>](cortypeattr-enumeration.md)  
 <span data-ttu-id="70af9-191">包含值，這些值表示類型中繼資料。</span><span class="sxs-lookup"><span data-stu-id="70af9-191">Contains values that indicate type metadata.</span></span>  
  
 [<span data-ttu-id="70af9-192">CorUnmanagedCallingConvention 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-192">CorUnmanagedCallingConvention Enumeration</span></span>](corunmanagedcallingconvention-enumeration.md)  
 <span data-ttu-id="70af9-193">包含值，這些值描述 Unmanaged 呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="70af9-193">Contains values that describe unmanaged calling conventions.</span></span>  
  
 [<span data-ttu-id="70af9-194">CorValidatorModuleType 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-194">CorValidatorModuleType Enumeration</span></span>](corvalidatormoduletype-enumeration.md)  
 <span data-ttu-id="70af9-195">提供[IMetaDataValidate](imetadatavalidate-interface.md)介面用來指定模組類型（PE 檔案與 .obj 檔案）的值。</span><span class="sxs-lookup"><span data-stu-id="70af9-195">Provides values used by the [IMetaDataValidate](imetadatavalidate-interface.md) interface to specify the type of the module (PE file vs. .obj file).</span></span>  
  
 [<span data-ttu-id="70af9-196">COUNINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="70af9-196">COUNINITIEE Enumeration</span></span>](couninitiee-enumeration.md)  
 <span data-ttu-id="70af9-197">指定初始化 common language runtime 時， [CoUninitializeEE](../hosting/couninitializeee-function.md)所使用的常數。</span><span class="sxs-lookup"><span data-stu-id="70af9-197">Specifies constants used by [CoUninitializeEE](../hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70af9-198">相關章節</span><span class="sxs-lookup"><span data-stu-id="70af9-198">Related Sections</span></span>  
 [<span data-ttu-id="70af9-199">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="70af9-199">Metadata Interfaces</span></span>](metadata-interfaces.md)  
  
 [<span data-ttu-id="70af9-200">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="70af9-200">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="70af9-201">中繼資料結構</span><span class="sxs-lookup"><span data-stu-id="70af9-201">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="70af9-202">中繼資料等位</span><span class="sxs-lookup"><span data-stu-id="70af9-202">Metadata Unions</span></span>](metadata-unions.md)

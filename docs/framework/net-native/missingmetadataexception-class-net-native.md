---
title: MissingMetadataException 類別 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 251d63fe8e025fe73b148c7deb368ab95ca3b1f7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049473"
---
# <a name="missingmetadataexception-class-net-native"></a><span data-ttu-id="3fd5a-102">MissingMetadataException 類別 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-102">MissingMetadataException Class (.NET Native)</span></span>

<span data-ttu-id="3fd5a-103">**適用于 Windows 10 的 Windows 應用程式的 .NET，僅限 .NET Native**</span><span class="sxs-lookup"><span data-stu-id="3fd5a-103">**.NET for Windows apps for Windows 10, .NET Native only**</span></span>

<span data-ttu-id="3fd5a-104">使用反映來擷取不存在的中繼資料時，所擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-104">The exception that is thrown when reflection is used to retrieve metadata that isn't present.</span></span>

<span data-ttu-id="3fd5a-105">**命名空間：** System.Reflection</span><span class="sxs-lookup"><span data-stu-id="3fd5a-105">**Namespace:** System.Reflection</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fd5a-106">`MissingMetadataException`類別僅供 .NET Native 工具鏈內部使用。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-106">The `MissingMetadataException` class is intended solely for internal use by the .NET Native tool chain.</span></span> <span data-ttu-id="3fd5a-107">這主要並非用於協力廠商程式碼中，也不應該在應用程式程式碼中處理此例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-107">It is not intended for use in third-party code, nor should you handle the exception in your application code.</span></span> <span data-ttu-id="3fd5a-108">相反地，請藉由將項目新增至[執行階段指示詞檔案](runtime-directives-rd-xml-configuration-file-reference.md)，來消除例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-108">Instead, you eliminate the exception by adding entries to your [runtime directives file](runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="3fd5a-109">如需詳細資訊，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-109">For more information, see the Remarks section.</span></span>

## <a name="syntax"></a><span data-ttu-id="3fd5a-110">語法</span><span class="sxs-lookup"><span data-stu-id="3fd5a-110">Syntax</span></span>

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

<span data-ttu-id="3fd5a-111">請注意 `MissingMetadataException` 類別衍生自 <xref:System.TypeAccessException>。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-111">Note that the `MissingMetadataException` class derives from <xref:System.TypeAccessException>.</span></span>

<span data-ttu-id="3fd5a-112">`MissingMetadataException` 類別具有下列成員：</span><span class="sxs-lookup"><span data-stu-id="3fd5a-112">The `MissingMetadataException` class has the following members:</span></span>

## <a name="constructors"></a><span data-ttu-id="3fd5a-113">建構函式</span><span class="sxs-lookup"><span data-stu-id="3fd5a-113">Constructors</span></span>

|<span data-ttu-id="3fd5a-114">建構函式</span><span class="sxs-lookup"><span data-stu-id="3fd5a-114">Constructor</span></span>|<span data-ttu-id="3fd5a-115">描述</span><span class="sxs-lookup"><span data-stu-id="3fd5a-115">Description</span></span>|
|-----------------|-----------------|
|`public MissingMetadataException()`|<span data-ttu-id="3fd5a-116">使用系統提供的錯誤說明訊息，初始化 `MissingMetadataException` 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-116">Initializes a new instance of the `MissingMetadataException` class by using a system-supplied message that describes the error.</span></span><br /><br /> <span data-ttu-id="3fd5a-117">此函式僅供 .NET Native 工具鏈內部使用。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-117">This constructor is for internal use by the .NET Native tool chain only.</span></span>|
|`public MissingMetadataException(String message)`|<span data-ttu-id="3fd5a-118">使用指定的錯誤訊息，初始化 `MissingMetadataException` 類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-118">Initializes a new instance of the `MissingMetadataException` class with a specified error message.</span></span><br /><br /> <span data-ttu-id="3fd5a-119">此函式僅供 .NET Native 工具鏈內部使用。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-119">This constructor is for internal use by the .NET Native tool chain only.</span></span>|

## <a name="properties"></a><span data-ttu-id="3fd5a-120">屬性</span><span class="sxs-lookup"><span data-stu-id="3fd5a-120">Properties</span></span>

|<span data-ttu-id="3fd5a-121">屬性</span><span class="sxs-lookup"><span data-stu-id="3fd5a-121">Property</span></span>|<span data-ttu-id="3fd5a-122">描述</span><span class="sxs-lookup"><span data-stu-id="3fd5a-122">Description</span></span>|
|--------------|-----------------|
|`public IDictionary Data { get; }`|<span data-ttu-id="3fd5a-123">取得提供例外狀況之其他使用者定義相關資訊的索引鍵/值組集合。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-123">Gets a collection of key/value pairs that provide additional user-defined information about the exception.</span></span> <span data-ttu-id="3fd5a-124">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-124">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public string HelpLink { get; set; }`|<span data-ttu-id="3fd5a-125">取得或設定與這個例外狀況相關聯的說明檔連結。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-125">Gets or sets a link to the help file associated with this exception.</span></span> <span data-ttu-id="3fd5a-126">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-126">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public int HResult { get; protected set; }`|<span data-ttu-id="3fd5a-127">取得或設定 `HRESULT`，這是指派給特定例外狀況的編碼數值。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-127">Gets or sets the `HRESULT`, a coded numeric value that is assigned to a specific exception.</span></span> <span data-ttu-id="3fd5a-128">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-128">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public Exception InnerException { get; }`|<span data-ttu-id="3fd5a-129">取得造成目前例外狀況的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-129">Gets the exception that caused the current exception.</span></span> <span data-ttu-id="3fd5a-130">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-130">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public string Message { get; }`|<span data-ttu-id="3fd5a-131">取得描述目前例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-131">Gets a message that describes the current exception.</span></span> <span data-ttu-id="3fd5a-132">(繼承自 <xref:System.TypeLoadException>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-132">(Inherited from <xref:System.TypeLoadException>.)</span></span>|
|`public string Source { get; set; }`|<span data-ttu-id="3fd5a-133">取得或設定造成錯誤的應用程式或物件名稱。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-133">Gets or sets the name of the application or object that caused the error.</span></span> <span data-ttu-id="3fd5a-134">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-134">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public string StackTrace { get; }`|<span data-ttu-id="3fd5a-135">取得呼叫堆疊上即時運算框架的字串表示。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-135">Gets a string representation of the immediate frames on the call stack.</span></span> <span data-ttu-id="3fd5a-136">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-136">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public MethodBase TargetSite { get; }`|<span data-ttu-id="3fd5a-137">取得擲回目前例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-137">Gets the method that threw the current exception.</span></span> <span data-ttu-id="3fd5a-138">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-138">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public string TypeName { get; ]`|<span data-ttu-id="3fd5a-139">取得遺失中繼資料之類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-139">Gets the fully qualified name of the type whose metadata is missing.</span></span> <span data-ttu-id="3fd5a-140">(繼承自 <xref:System.TypeLoadException>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-140">(Inherited from <xref:System.TypeLoadException>.)</span></span>|

## <a name="methods"></a><span data-ttu-id="3fd5a-141">方法</span><span class="sxs-lookup"><span data-stu-id="3fd5a-141">Methods</span></span>

|<span data-ttu-id="3fd5a-142">方法</span><span class="sxs-lookup"><span data-stu-id="3fd5a-142">Method</span></span>|<span data-ttu-id="3fd5a-143">描述</span><span class="sxs-lookup"><span data-stu-id="3fd5a-143">Description</span></span>|
|------------|-----------------|
|`public bool Equals(Object obj)`|<span data-ttu-id="3fd5a-144">判斷指定的物件是否等於目前的物件。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-144">Determines whether the specified object is equal to the current object.</span></span>  <span data-ttu-id="3fd5a-145">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-145">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`protected void Finalize()`|<span data-ttu-id="3fd5a-146">在記憶體回收開始前，允許物件嘗試釋放資源，並執行其他清除作業。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-146">Allows an object to try to free resources and perform other cleanup operations before it is reclaimed by garbage collection.</span></span> <span data-ttu-id="3fd5a-147">(繼承自 <xref:System.Object>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-147">(Inherited from <xref:System.Object>.)</span></span>|
|`public Exception GetBaseException()`|<span data-ttu-id="3fd5a-148">傳回一或多個後續例外狀況之根本原因的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-148">Returns the exception that is the root cause of one or more subsequent exceptions.</span></span> <span data-ttu-id="3fd5a-149">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-149">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`public int GetHashCode()`|<span data-ttu-id="3fd5a-150">傳回 `MissingMetadataException` 執行個體的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-150">Returns a hash code for a `MissingMetadataException` instance.</span></span>   <span data-ttu-id="3fd5a-151">(繼承自 <xref:System.Object>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-151">(Inherited from <xref:System.Object>.)</span></span>|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|<span data-ttu-id="3fd5a-152">使用與例外狀況相關的資訊來設定 <xref:System.Runtime.Serialization.SerializationInfo> 物件。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-152">Sets a <xref:System.Runtime.Serialization.SerializationInfo> object with information about the exception.</span></span>  <span data-ttu-id="3fd5a-153">(繼承自 <xref:System.TypeLoadException>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-153">(Inherited from <xref:System.TypeLoadException>.)</span></span>|
|`public Type GetType()`|<span data-ttu-id="3fd5a-154">取得目前執行個體的執行階段類型。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-154">Gets the runtime type of the current instance.</span></span> <span data-ttu-id="3fd5a-155">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-155">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|
|`protected Object MemberwiseClone()`|<span data-ttu-id="3fd5a-156">建立目前物件的淺層複本。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-156">Creates a shallow copy of the current object.</span></span> <span data-ttu-id="3fd5a-157">(繼承自 <xref:System.Object>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-157">(Inherited from <xref:System.Object>.)</span></span>|
|`public string ToString()`|<span data-ttu-id="3fd5a-158">傳回目前例外狀況的字串表示。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-158">Returns the string representation of the current exception.</span></span> <span data-ttu-id="3fd5a-159">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-159">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|

## <a name="events"></a><span data-ttu-id="3fd5a-160">事件</span><span class="sxs-lookup"><span data-stu-id="3fd5a-160">Events</span></span>

|<span data-ttu-id="3fd5a-161">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="3fd5a-161">Event</span></span>|<span data-ttu-id="3fd5a-162">描述</span><span class="sxs-lookup"><span data-stu-id="3fd5a-162">Description</span></span>|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|<span data-ttu-id="3fd5a-163">當例外狀況序列化，以建立包含例外狀況相關序列化資料的例外狀況狀態物件時，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-163">Occurs when an exception is serialized to create an exception state object that contains serialized data about the exception.</span></span> <span data-ttu-id="3fd5a-164">(繼承自 <xref:System.Exception?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="3fd5a-164">(Inherited from <xref:System.Exception?displayProperty=nameWithType>.)</span></span>|

## <a name="usage-details"></a><span data-ttu-id="3fd5a-165">用法詳細資料</span><span class="sxs-lookup"><span data-stu-id="3fd5a-165">Usage Details</span></span>

<span data-ttu-id="3fd5a-166">使用反映來存取組件中沒有的中繼資料時，就會擲回 `MissingMetadataException` 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-166">The `MissingMetadataException` exception is thrown when reflection is used to access metadata that isn’t available in an assembly.</span></span>

<span data-ttu-id="3fd5a-167">應用程式在執行時間可使用的中繼資料是由執行時間指示詞（XML 設定）檔案（ \*app.config）所定義。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-167">The metadata that is available to an app at run time is defined by the runtime directives (XML configuration) file, \*.rd.xml.</span></span> <span data-ttu-id="3fd5a-168">若要防止您的應用程式擲回這個例外狀況，您必須修改 \*.rd.xml，以定義必須出現在執行階段的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-168">To prevent your app from throwing this exception, you must modify \*.rd.xml to define the metadata that must be present at run time.</span></span> <span data-ttu-id="3fd5a-169">如需 \*.rd.xml 檔案格式的資訊，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-169">For information about the format of the \*.rd.xml file, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fd5a-170">因為這個例外狀況指出應用程式所需的中繼資料在執行階段無法使用，所以您不應該在 `try`/`catch` 區塊中處理這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-170">Because this exception indicates that metadata needed by your application isn’t available at run time, you shouldn’t handle this exception in a `try`/`catch` block.</span></span> <span data-ttu-id="3fd5a-171">相反地，您應該診斷例外狀況的原因，然後透過執行階段指示詞檔案來去除這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-171">Instead, you should diagnose the cause of the exception and eliminate it by using a runtime directives file.</span></span> <span data-ttu-id="3fd5a-172">若要取得可加入執行階段指示詞檔案以消除例外狀況的項目，您可以使用下列兩個疑難排解工具之一：</span><span class="sxs-lookup"><span data-stu-id="3fd5a-172">To get the entry that you can add to your runtime directives file that eliminates the exception, you can use one of two troubleshooters:</span></span>
>
> - <span data-ttu-id="3fd5a-173">針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-173">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>
> - <span data-ttu-id="3fd5a-174">針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-174">The [MissingMetadataException troubleshooter](https://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>

<span data-ttu-id="3fd5a-175">`MissingMetadataException` 類別沒有包含唯一成員；其所有成員都是繼承自其基底類別 <xref:System.TypeAccessException>。</span><span class="sxs-lookup"><span data-stu-id="3fd5a-175">The `MissingMetadataException` class contains no unique members; all of its members are inherited from its base class, <xref:System.TypeAccessException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fd5a-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fd5a-176">See also</span></span>

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [<span data-ttu-id="3fd5a-177">MissingInteropDataException 類別</span><span class="sxs-lookup"><span data-stu-id="3fd5a-177">MissingInteropDataException Class</span></span>](missinginteropdataexception-class-net-native.md)
- [<span data-ttu-id="3fd5a-178">MissingRuntimeArtifactException 類別</span><span class="sxs-lookup"><span data-stu-id="3fd5a-178">MissingRuntimeArtifactException Class</span></span>](missingruntimeartifactexception-class-net-native.md)
- [<span data-ttu-id="3fd5a-179">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="3fd5a-179">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
